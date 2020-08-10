<h4 id="msg">加载中...</h4><script src="https://cdn.staticfile.org/jquery/3.4.0/jquery.min.js"></script>
<script>
  function getQueryVariable(variable) {
    var query = window.location.search.substring(1);
    var vars = query.split("&");
    for (var i = 0; i < vars.length; i++) {
      var pair = vars[i].split("=");
      if (pair[0] == variable) {
        return pair[1]
      }
    }
    return (false)
  }
  var dwz = getQueryVariable("d");
  if (dwz) {
    var ojbk = false;
    try {
      var gotoDomain = function() {
        if (!ojbk) {
          $.ajax({
            type: "get",
            async: false,
            url: "https://dy.XXXXXXX.cn/ss/douyin/"+dwz+"/to",
            dataType: "text",
            success: function(longurl) {
              if (!ojbk) {
                ojbk = true;
                var gotoUrl = longurl;
                window.location.replace(gotoUrl)
              }
            },
            error: function() {
              if (!ojbk) {
                ojbk = true;
                $("#msg").html("获取最新域名失败")
              }
            }
          })
        }
      };
      gotoDomain();
      setInterval(gotoDomain, 2000)
    } catch(err) {
      ojbk = true;
      $("#msg").html("发生错误了");
      alert(err)
    }
  } else {
    $("#msg").html("无效的数据")
  };
</script>
