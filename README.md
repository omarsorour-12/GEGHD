# إنشاء ملف HTML لموقع التحكم في الإضاءة
smart_light_html = """<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>غرفتي الذكية - التحكم في الإضاءة</title>
  <style>
    body {
      font-family: Tahoma, sans-serif;
      background-color: #f5f5f5;
      text-align: center;
      padding: 50px;
    }
    .room {
      background-color: #fff;
      border-radius: 12px;
      padding: 40px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      display: inline-block;
    }
    .light-status {
      font-size: 24px;
      margin: 20px 0;
    }
    .light-on {
      color: green;
    }
    .light-off {
      color: red;
    }
    button {
      padding: 15px 30px;
      margin: 10px;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    .on-btn {
      background-color: #28a745;
      color: white;
    }
    .off-btn {
      background-color: #dc3545;
      color: white;
    }
    .lightbulb {
      font-size: 60px;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <div class="room">
    <h1>غرفتي الذكية</h1>
    <p class="light-status light-off" id="status">الإضاءة مطفأة ❌</p>
    <button class="on-btn" onclick="turnOn()">تشغيل الإضاءة</button>
    <button class="off-btn" onclick="turnOff()">إيقاف الإضاءة</button>
    <div class="lightbulb" id="bulb">💡</div>
  </div>

  <script>
    function turnOn() {
      document.getElementById("status").textContent = "الإضاءة تعمل ✅";
      document.getElementById("status").className = "light-status light-on";
      document.getElementById("bulb").textContent = "💡";
    }

    function turnOff() {
      document.getElementById("status").textContent = "الإضاءة مطفأة ❌";
      document.getElementById("status").className = "light-status light-off";
      document.getElementById("bulb").textContent = "💡";
    }
  </script>

</body>
</html>
"""

# حفظ الملف
html_path = "/mnt/data/smart_room.html"
with open(html_path, "w", encoding="utf-8") as f:
    f.write(smart_light_html)

# ضغطه إلى ملف ZIP
zip_path = "/mnt/data/smart_room_site.zip"
with ZipFile(zip_path, "w") as zipf:
    zipf.write(html_path, arcname="index.html")

zip_path
