
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>เป็นแฟนกันมั้ย 💗</title>
<style>
*{box-sizing:border-box}
body{
  margin:0;min-height:100vh;display:grid;
  place-items:center;text-align:center;
  font-family:Arial,sans-serif;
  background:linear-gradient(135deg,#ffe0eb,#fff5f8);
  color:#bd426e;overflow:hidden
}
main{width:92%;max-width:450px;padding:20px}
.page{display:none}
.page.active{display:block;animation:fade .5s}
@keyframes fade{
  from{opacity:0;transform:translateY(15px)}
  to{opacity:1;transform:translateY(0)}
}
h1{font-size:30px}
p{line-height:1.8}
button{
  border:0;border-radius:30px;padding:14px 24px;
  font-size:17px;font-weight:bold;cursor:pointer;
  margin:8px;transition:.25s
}
.open{background:#ff6b9b;color:white}
.yes{background:#ff5790;color:white}
.no{background:white;color:#bd426e}
.envelope{
  position:relative;width:220px;height:145px;
  margin:40px auto;background:#ff8eb2;
  border-radius:8px;box-shadow:0 8px 20px #e76b9533
}
.envelope:after{
  content:"";position:absolute;inset:0;
  background:#ffb3cb;
  clip-path:polygon(0 0,50% 60%,100% 0);
}
.letter{
  position:absolute;z-index:0;left:15%;top:10px;
  width:70%;height:100px;background:white;
  display:grid;place-items:center;font-size:35px;
  transition:.6s
}
.envelope.open .letter{transform:translateY(-65px)}
.heart{position:fixed;bottom:-30px;animation:up 6s linear infinite}
@keyframes up{to{transform:translateY(-110vh);opacity:0}}
</style>
</head>
<body>
<main>
  <section class="page active" id="page1">
    <h1>มีจดหมายถึงเธอ 💌</h1>
    <div class="envelope" id="envelope">
      <div class="letter">💗</div>
    </div>
    <p>ลองเปิดดูสิ มีอะไรอยากบอก...</p>
    <button class="open" onclick="openLetter()">
      ลองเปิดดู 💌
    </button>
  </section>

  <section class="page" id="page2">
    <h1>เป็นแฟนกันมั้ยย 🥺💖</h1>
    <p>เราอยากมีเธออยู่ในทุก ๆ วัน<br>
    ให้โอกาสเราได้ดูแลเธอนะ 💕</p>
    <button class="yes" id="yes" onclick="accept()">
      เป็น 💖
    </button>
    <button class="no" id="no" onclick="reject()">
      ไม่เป็น 🥺
    </button>
    <p id="message"></p>
  </section>

  <section class="page" id="page3">
    <h1>เย้ ๆๆๆ 💖🥰</h1>
    <p>ขอบคุณที่ตอบตกลงนะะ<br>
    ต่อจากนี้มีเราอยู่ด้วยกันนะ 💗</p>
    <div style="font-size:60px">💐💞🌷</div>
    <button class="open" onclick="location.reload()">
      อ่านอีกครั้ง 💌
    </button>
  </section>
</main>

<script>
function showPage(id){
  document.querySelectorAll('.page').forEach(p=>{
    p.classList.remove('active');
  });
  document.getElementById(id).classList.add('active');
}

function openLetter(){
  document.getElementById('envelope').classList.add('open');
  setTimeout(()=>showPage('page2'),600);
}

let size=1;
let count=0;

function reject(){
  count++;
  size=Math.min(size+0.3,3.5);

  const yes=document.getElementById('yes');
  yes.style.transform=`scale(${size})`;

  const messages=[
    'ลองคิดดูอีกทีน้า 🥺',
    'แน่ใจเหรออ 💗',
    'เป็นแฟนกันนะะ 💖',
    'ปุ่มเป็นรออยู่น้าา 🥹'
  ];

  document.getElementById('message').textContent=
    messages[(count-1)%messages.length];
}

function accept(){
  showPage('page3');
  for(let i=0;i<25;i++){
    const h=document.createElement('div');
    h.className='heart';
    h.textContent=['💗','💕','💖','🌸'][i%4];
    h.style.left=Math.random()*100+'%';
    h.style.animationDelay=Math.random()*3+'s';
    h.style.fontSize=(20+Math.random()*20)+'px';
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),7000);
  }
}
</script>
</body>
</html>
