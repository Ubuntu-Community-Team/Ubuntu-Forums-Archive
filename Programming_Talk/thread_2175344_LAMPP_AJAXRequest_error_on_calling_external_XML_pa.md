---
title: "LAMPP AJAXRequest error on calling external XML page"
date: 2013-09-18
forum: Programming Talk
---

### Post by shayno90 on 2013-09-18
[COLOR=#000000][FONT=Verdana]I am testing out AJAX request to get an XML page but it fails to retrieve the XML page (the url with XML content is accessible via the browser).[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]How can I adjust the ajaxrequest to parse the XML page request?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Exact error is "Ajax error: no data received"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code works when adjusted for normal HTTP webpage call.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]PHP File1:
[/FONT][/COLOR]```
<html>
    <head>
        <meta http-equiv="Content-Type" xml version="1.0"
              content="text/xml; charset=UTF-8">
        
        <title></title>
    </head>
    <body>
        <?php
        if (isset($_GET['url'])) {
            header('Content-Type: text/xml');
            echo file_get_contents("http://".SanitizeString($_GET['url']));
        }
        
        function SanitizeString ($var) {
            $var = strip_tags($var);
            $var = htmlentities($var);
            return stripslashes($var);
        }
        ?>
    </body>
</html>

[FONT=Verdana]
[/FONT]
```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR][FONT=Verdana]PHP File2
[/FONT]```

<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" xml version="1.0"
              content="text/xml; charset=UTF-8">
        <title>Ajax XML example</title>
        
    </head>
    <body>
       <center />
        <h2> Loading XML content into a DIV</h2>
        <div id='info'>This sentence will be replaced</div>
        <script>
            
            nocache = "&nocache=" + Math.random() * 1000000
            url = "rss.news.yahoo.com/rss/topstories"
            request = new ajaxRequest()
            request.open("GET", "xmlget.php?url=" + url + nocache, true)
            //request.setRequestHeader("Content-type", "text/xml")
            out = "";
            
request.onreadystatechange = function()
{
     if (this.readyState == 4)
     {
         if (this.status == 200)
         {
             if (this.responseXML != null)
             {
                 titles = this.responseXML.getElementsByTagName('title')
                                    
                 for (j = 0 ; j < titles.length ; ++j)
                 {
                      out += titles[j].childNodes[0].nodeValue + '<br />'
                 }
                 document.getElementById('info').innerHTML = out
             }
             else alert("Ajax error: No data received")
          }
          else alert("Ajax error: " + this.statusText)
      }
}
            
request.send(null)
            
function ajaxRequest()
  {
   try
   {
         var request = new XMLHttpRequest()
   }
   catch(e1)
   {
        try
        {
             request = new ActiveXobject("Msxml2.XMLHTTP")
        }
        catch(e2)
        {
            try
            {
                 request = new ActiveXObject("Microsoft.XMLHTTP")
            }
            catch(e3)
            {
                request = false
            }
         }
    }
     return request
}
      </script>
      <?php
        // put your code here
        ?>
        </body>
</html>
```

---

