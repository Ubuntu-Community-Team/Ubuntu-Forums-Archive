---
title: "html: background from local filesystem"
date: 2010-09-20
forum: Programming Talk
---

### Post by angustia on 2010-09-20
hi everyone.

the question: 

how can i make (with html and js) a way that lets the user select an image from his local filesystem and set it as background... all this without going through the web server?

(i want to know if there's a way to do it or i'm forced to make a server side)

more context:
i'm new in this about web programming and i'm trying to make a simple application to do this thing:

- the user selects a picture from his local FS
- the picture is loaded en the page and de user selects some points
- the page makes some math calculations and presents the results
- all this in one html+js web page, without server side (i think it doesn't justify uploading the image to a server just to be served back again).

thanks for any help.
excuse my english.

---

### Post by worksofcraft on 2010-09-20
The recommended way to set background images is in CSS, but you can do it straight in the html and you can get Javascript to write that html as it loads using documemt.write()

I won't attempt the Javascript coding, but here is some html to display a local file as background image to get you started:
 
```

<html><head>
	<title>background image test</title>
</head><body background="file:///usr/share/backgrounds/Daisy.jpg">
</body></html>

```

---

### Post by angustia on 2010-09-20
> **worksofcraft said:**
> The recommended way to set background images is in CSS, but you can do it straight in the html and you can get Javascript to write that html as it loads using documemt.write()

I won't attempt the Javascript coding, but here is some html to display a local file as background image to get you started:
 
```

<html><head>
	<title>background image test</title>
</head><body background="file:///usr/share/backgrounds/Daisy.jpg">
</body></html>

```

i'm setting the background with an initial image; also i put a form in the page with an input (type="file") to let the user select an image, but i don't know how to capture the selected file path... and some people suggested that security concerns make it impossible to capture and read that path...

---

### Post by worksofcraft on 2010-09-20
> **angustia said:**
> i'm setting the background with an initial image; also i put a form in the page with an input (type="file") to let the user select an image, but i don't know how to capture the selected file path... and some people suggested that security concerns make it impossible to capture and read that path...

You **can** select files from your local system. e.g. try "Manage Attachments" on these Ubuntu forums. Right click the page and try "view source" to see how they did it... admittedly it all looks rather ghastly and unintelligible to me (like most things Javascript), but I heard some people can actually understand it :shock:

---

### Post by Tibuda on 2010-09-21
here's an example. it only works on firefox, not chrome.
```
<html>
<head>
<title>title</title>
<script type="text/javascript" language="javascript" charset="utf-8">
// <![CDATA[
function file_change()
{
  var filename = document.getElementById('filename');
  var preview =  document.getElementById('preview');
  if (filename.files)
  {
    preview.src = filename.files.item(0).getAsDataURL();
  }
  else
  {
    preview.src = filename.value;
  }
}
// ]]>
</script>
</head>
<body>
  <form action="get" method="#">
    <input type="file" id="filename" onchange="file_change();" />
  </form>
  <img id="preview" src="#" alt="preview" />
    
 </body>
</html>
```

---

### Post by angustia on 2010-09-21
> **worksofcraft said:**
> You **can** select files from your local system. e.g. try "Manage Attachments" on these Ubuntu forums. Right click the page and try "view source" to see how they did it... admittedly it all looks rather ghastly and unintelligible to me (like most things Javascript), but I heard some people can actually understand it :shock:

i was looking in that code, and i could get the name of the filename but not the complete path... and it seems that it's that way by security design.

now, i found this [hack]("http://demos.hacks.mozilla.org/openweb/imageUploader/") that uses drag an drop to load a local image, works in chrome too and happens to work offline too...

---

