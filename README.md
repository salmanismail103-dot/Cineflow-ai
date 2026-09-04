<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CineFlow AI</title>

<style>
*{box-sizing:border-box}
body{
    margin:0;
    font-family:Arial,sans-serif;
    background:#0b0b12;
    color:#fff;
}
header{
    padding:20px;
    text-align:center;
    border-bottom:1px solid #292936;
}
.logo{
    font-size:28px;
    font-weight:bold;
}
.logo span{color:#8b5cf6}
.container{
    max-width:900px;
    margin:auto;
    padding:25px 18px;
}
.hero{
    text-align:center;
    padding:30px 0;
}
.hero h1{
    font-size:38px;
    margin-bottom:10px;
}
.hero p{
    color:#aaa;
    font-size:17px;
}
.card{
    background:#15151f;
    border:1px solid #292936;
    border-radius:18px;
    padding:22px;
    margin-top:20px;
}
label{
    display:block;
    margin-bottom:10px;
    font-weight:bold;
}
textarea{
    width:100%;
    min-height:130px;
    resize:vertical;
    background:#0d0d15;
    color:white;
    border:1px solid #333342;
    border-radius:12px;
    padding:15px;
    font-size:16px;
    outline:none;
}
textarea:focus{
    border-color:#8b5cf6;
}
button{
    border:0;
    border-radius:12px;
    padding:14px 20px;
    font-size:16px;
    cursor:pointer;
    font-weight:bold;
}
.primary{
    background:#8b5cf6;
    color:white;
    width:100%;
    margin-top:15px;
}
.primary:hover{background:#7c3aed}
.result{
    display:none;
}
.scene{
    background:#0d0d15;
    border:1px solid #292936;
    border-radius:14px;
    padding:16px;
    margin-top:12px;
}
.scene h3{
    margin-top:0;
    color:#a78bfa;
}
.prompt{
    color:#bbb;
    line-height:1.7;
}
.badge{
    display:inline-block;
    background:#251b3d;
    color:#c4b5fd;
    padding:7px 12px;
    border-radius:20px;
    margin:4px;
    font-size:13px;
}
.loading{
    text-align:center;
    color:#a78bfa;
    display:none;
}
footer{
    text-align:center;
    padding:30px;
    color:#666;
}
</style>
</head>

<body>

<header>
    <div class="logo">Cine<span>Flow</span> AI 🎬</div>
</header>

<div class="container">

<section class="hero">
    <h1>حوّل فكرتك إلى فيلم 🎥</h1>
    <p>
        اكتب فكرتك، ودع CineFlow AI يحولها إلى قصة ومشاهد وPrompts جاهزة.
    </p>
</section>

<div class="card">
    <label>💡 ما هي فكرة فيلمك؟</label>

    <textarea id="idea"
    placeholder="مثال: شاب يحب فتاة لكنه يخفي عنها حقيقة مؤلمة، وبعد سنوات يلتقيان مجددًا..."></textarea>

    <button class="primary" onclick="generateStory()">
        ✨ إنشاء الفيلم
    </button>

    <div class="loading" id="loading">
        ⏳ جاري بناء القصة والمشاهد...
    </div>
</div>

<div class="card result" id="result">

    <h2>🎬 النتيجة</h2>

    <div id="story"></div>

    <h2>🎞️ المشاهد</h2>

    <div id="scenes"></div>

</div>

</div>

<footer>
    CineFlow AI — Your idea. Your story. Your film.
</footer>

<script>

function generateStory(){

    const idea = document.getElementById("idea").value.trim();

    if(!idea){
        alert("اكتب فكرة الفيلم أولاً ✍️");
        return;
    }

    document.getElementById("loading").style.display="block";
    document.getElementById("result").style.display="none";

    setTimeout(function(){

        document.getElementById("loading").style.display="none";
        document.getElementById("result").style.display="block";

        document.getElementById("story").innerHTML = `
            <div class="scene">
                <h3>📖 فكرة القصة</h3>
                <p>${idea}</p>
            </div>

            <div class="scene">
                <h3>🎭 نوع الفيلم</h3>
                <span class="badge">دراما</span>
                <span class="badge">رومانسي</span>
                <span class="badge">سينمائي</span>
            </div>

            <div class="scene">
                <h3>📝 ملخص</h3>
                <p>
                تبدأ القصة من فكرة مليئة بالمشاعر والصراع الداخلي.
                تتطور الأحداث تدريجيًا، وتواجه الشخصيات قرارات صعبة
                تقود إلى لحظة عاطفية حاسمة في النهاية.
                </p>
            </div>
        `;

        document.getElementById("scenes").innerHTML = `

        <div class="scene">
            <h3>المشهد 1 — البداية</h3>
            <p>
            لقطة سينمائية واسعة للمكان، تظهر الشخصية الرئيسية
            وهي تعيش حياتها قبل بداية الأحداث.
            </p>
            <p class="prompt">
            🎨 Prompt:<br>
            cinematic movie scene, realistic character,
            emotional atmosphere, dramatic lighting,
            detailed environment, 4K, film look
            </p>
        </div>

        <div class="scene">
            <h3>المشهد 2 — اللقاء</h3>
            <p>
            تلتقي الشخصيات الرئيسية في لحظة غير متوقعة،
            وتظهر على وجوههم علامات الدهشة والمشاعر المخفية.
            </p>
            <p class="prompt">
            🎨 Prompt:<br>
            emotional cinematic encounter, two characters,
            realistic facial expressions, soft lighting,
            shallow depth of field, cinematic composition
            </p>
        </div>

        <div class="scene">
            <h3>المشهد 3 — الصراع</h3>
            <p>
            تظهر المشكلة الرئيسية، ويبدأ الصراع الداخلي
            بين الشخصيات والقرارات التي يجب اتخاذها.
            </p>
            <p class="prompt">
            🎨 Prompt:<br>
            dramatic emotional scene, intense expressions,
            cinematic shadows, realistic environment,
            movie still, high detail, 4K
            </p>
        </div>

        <div class="scene">
            <h3>المشهد 4 — النهاية</h3>
            <p>
            تصل القصة إلى لحظتها الأكثر تأثيرًا،
            وتترك النهاية أثرًا عاطفيًا لدى المشاهد.
            </p>
            <p class="prompt">
            🎨 Prompt:<br>
            emotional cinematic ending, powerful atmosphere,
            dramatic lighting, realistic characters,
            beautiful composition, movie masterpiece
            </p>
        </div>

        `;

    },1000);
}

</script>

</body>
</html>
