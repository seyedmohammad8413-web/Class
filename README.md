<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>آزمون آنلاین</title>

    <style>
        * {
            box-sizing: border-box;
            font-family: Tahoma, Arial, sans-serif;
        }

        body {
            margin: 0;
            background: #f2f4f8;
            color: #222;
        }

        header {
            background: #4f46e5;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .container {
            max-width: 800px;
            margin: 30px auto;
            padding: 20px;
        }

        .info {
            background: white;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
        }

        .timer {
            color: #e11d48;
            font-weight: bold;
        }

        .question {
            background: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.08);
        }

        .question h2 {
            margin-top: 0;
        }

        .option {
            display: block;
            background: #f8fafc;
            padding: 15px;
            margin: 12px 0;
            border-radius: 10px;
            cursor: pointer;
            border: 2px solid transparent;
        }

        .option:hover {
            background: #eef2ff;
            border-color: #6366f1;
        }

        .option input {
            margin-left: 10px;
        }

        button {
            width: 100%;
            padding: 15px;
            margin-top: 20px;
            border: none;
            border-radius: 10px;
            background: #4f46e5;
            color: white;
            font-size: 17px;
            cursor: pointer;
        }

        button:hover {
            background: #3730a3;
        }

        #result {
            display: none;
            background: white;
            padding: 30px;
            text-align: center;
            border-radius: 15px;
        }

        .score {
            font-size: 35px;
            color: #16a34a;
            font-weight: bold;
        }
    </style>
</head>

<body>

<header>
    <h1>📝 آزمون آنلاین</h1>
    <p>به آزمون خوش آمدید</p>
</header>

<div class="container">

    <div class="info">
        <span>تعداد سؤالات: 5</span>
        <span class="timer">⏱ زمان: <span id="time">02:00</span></span>
    </div>

    <div id="exam">

        <div class="question">
            <h2>1. پایتخت ایران کدام است؟</h2>

            <label class="option">
                <input type="radio" name="q1" value="0">
                شیراز
            </label>

            <label class="option">
                <input type="radio" name="q1" value="1">
                تهران
            </label>

            <label class="option">
                <input type="radio" name="q1" value="0">
                اصفهان
            </label>

            <label class="option">
                <input type="radio" name="q1" value="0">
                تبریز
            </label>
        </div>


        <div class="question">
            <h2>2. حاصل 5 × 4 چند است؟</h2>

            <label class="option">
                <input type="radio" name="q2" value="0">
                15
            </label>

            <label class="option">
                <input type="radio" name="q2" value="1">
                20
            </label>

            <label class="option">
                <input type="radio" name="q2" value="0">
                25
            </label>

            <label class="option">
                <input type="radio" name="q2" value="0">
                30
            </label>
        </div>


        <div class="question">
            <h2>3. زبان ساختار صفحات وب چیست؟</h2>

            <label class="option">
                <input type="radio" name="q3" value="1">
                HTML
            </label>

            <label class="option">
                <input type="radio" name="q3" value="0">
                Python
            </label>

            <label class="option">
                <input type="radio" name="q3" value="0">
                Java
            </label>

            <label class="option">
                <input type="radio" name="q3" value="0">
                C++
            </label>
        </div>


        <div class="question">
            <h2>4. زمین به دور چه چیزی می‌چرخد؟</h2>

            <label class="option">
                <input type="radio" name="q4" value="1">
                خورشید
            </label>

            <label class="option">
                <input type="radio" name="q4" value="0">
                ماه
            </label>

            <label class="option">
                <input type="radio" name="q4" value="0">
                مریخ
            </label>

            <label class="option">
                <input type="radio" name="q4" value="0">
                مشتری
            </label>
        </div>


        <div class="question">
            <h2>5. کدام مورد یک مرورگر اینترنتی است؟</h2>

            <label class="option">
                <input type="radio" name="q5" value="1">
                Chrome
            </label>

            <label class="option">
                <input type="radio" name="q5" value="0">
                Photoshop
            </label>

            <label class="option">
                <input type="radio" name="q5" value="0">
                Word
            </label>

            <label class="option">
                <input type="radio" name="q5" value="0">
                Excel
            </label>
        </div>

        <button onclick="submitExam()">ثبت آزمون</button>

    </div>


    <div id="result">
        <h2>🎉 آزمون به پایان رسید</h2>
        <p>نمره شما:</p>

        <div class="score">
            <span id="score">0</span> از 5
        </div>

        <button onclick="location.reload()">آزمون مجدد</button>
    </div>

</div>


<script>

let time = 120;

let timer = setInterval(function() {

    let minutes = Math.floor(time / 60);
    let seconds = time % 60;

    seconds = seconds < 10 ? "0" + seconds : seconds;

    document.getElementById("time").innerText =
        minutes + ":" + seconds;

    if (time <= 0) {
        clearInterval(timer);
        submitExam();
    }

    time--;

}, 1000);


function submitExam() {

    clearInterval(timer);

    let score = 0;

    for (let i = 1; i <= 5; i++) {

        let answer = document.querySelector(
            'input[name="q' + i + '"]:checked'
        );

        if (answer) {
            score += Number(answer.value);
        }
    }

    document.getElementById("exam").style.display = "none";

    document.getElementById("result").style.display = "block";

    document.getElementById("score").innerText = score;
}

</script>

</body>
</html>
