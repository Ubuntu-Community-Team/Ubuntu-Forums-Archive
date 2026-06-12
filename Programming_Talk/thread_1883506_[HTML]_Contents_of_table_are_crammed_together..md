---
title: "[HTML] Contents of table are crammed together."
date: 2011-11-19
forum: Programming Talk
---

### Post by ki4jgt on 2011-11-19
First of all, this deals with a free tarot reading site. I do not believe in the Tarot's ability to foresee the future, (for anyone who does believe in the Tarot) but I do believe in it's ability to point out hidden feelings a person may have about the world around them, and it provides a means to allow this person to confront these feelings. That being said, I have setup a site (for my own amusement as well as the people who use the site) but the table's contents aren't going 100% as I have set the table width to do. I was wondering if I could get one of you guy's help to achieve this.

```
<html>
	<head>
		<title>FREE Tarot Readings</title>
	</head>
	<body>
		<div id="fb-root"></div>
		<script>(function(d, s, id) {
		  var js, fjs = d.getElementsByTagName(s)[0];
		  if (d.getElementById(id)) {return;}
		  js = d.createElement(s); js.id = id;
		  js.src = "//connect.facebook.net/eo_EO/all.js#xfbml=1&appId=242681372441941";
		  fjs.parentNode.insertBefore(js, fjs);
		}(document, 'script', 'facebook-jssdk'));</script>
		<table width = "100%">
			<tr>
				<td><h1>Welcome to CardReadings</h1></td>
				<td><div class="fb-like" data-href="http://www.cardreadings.co.cc"
				data-send="true" data-layout="button_count" data-width="450"
				data-show-faces="true" data-colorscheme="dark"></div></td>
			</tr>
			<tr>
				<td><strong>This service is for entertainment purposes ONLY!</strong> - This 					service has been setup for your enjoyment. We at
				<a href = "http://www.cardreadings.co.cc">CardReadings</a>
				<strong>DO NOT</strong> believe that mere pieces of cardboard may determine how 				your life is to be run. Instead, we believe that the 
				<a href = "http://en.wikipedia.org/wiki/Forer_effect">Forer Effect</a>
				applies to Tarot cards and that you should only use them to uncover hidden 					aspects about yourself. We see it as a form of psychological reflection. We are 				not licensed psychologists.</td>
				<td><script type="text/javascript"><!--
				google_ad_client = "ca-pub-6585656879572934";
				/* CardReadingsSite */
				google_ad_slot = "3441394495";
				google_ad_width = 160;
				google_ad_height = 600;
				//-->
				</script>
				<script type="text/javascript"
				src="http://pagead2.googlesyndication.com/pagead/show_ads.js">
				</script></td>
			</tr>
			<tr>
				<td cellspan = "2">Please email me with your requests
				<a href = "mailto:admin@cardreadings.co.cc">HERE</a>
			</tr>
			<tr>
				<td cellspan = "2"><script language="JavaScript">var e=unescape("%AE%E1%E6%EB%FE%F7%B2%E6%EB%E2%F7%AF%B0%E6%F7%EA%E6%BD%F1%E1%E1%B0%AC%AE%B3%BF%BF%98%BC%E7%CD%D1%F3%E0%F6%C0%F7%F3%F6%FB%FC%F5%E1%B2%D3%BE%B2%D3%A8%FE%FB%FC%F9%BE%D3%A8%E4%FB%E1%FB%E6%F7%F6%BE%D3%A8%F3%F1%E6%FB%E4%F7%BE%D3%A8%FA%FD%E4%F7%E0%E9%98%F1%FD%FE%FD%E0%A8%B2%B1%A2%A1%A2%A2%D6%D4%A9%F4%FD%FC%E6%BF%F4%F3%FF%FB%FE%EB%A8%B2%D3%E0%FB%F3%FE%A9%F4%FD%FC%E6%BF%E1%FB%E8%F7%A8%B2%A3%A0%E2%EA%A9%98%EF%98%BF%BF%AC%AE%BD%E1%E6%EB%FE%F7%AC%98%AE%E1%F1%E0%FB%E2%E6%AC%98%E4%F3%E0%B2%E6%F6%FD%F8%B2%AF%B2%FC%F7%E5%B2%D6%F3%E6%F7%BA%BB%A9%98%E4%F3%E0%B2%D3%F6%E1%CD%E0%F3%E6%FB%F7%B2%AF%B2%E6%F6%FD%F8%B2%BD%B2%A3%A2%A2%A2%B2%BD%B2%A4%A2%A9%98%E4%F3%E0%B2%D3%F6%F1%E1%B2%AF%B2%D3%F6%E1%CD%E0%F3%E6%FB%F7%B2%BD%B2%A4%A2%A9%98%E4%F3%E0%B2%FF%EB%DA%F7%FB%F5%FA%E6%AF%A2%A9%FB%F4%BA%E6%EB%E2%F7%FD%F4%BA%E5%FB%FC%F6%FD%E5%BC%FB%FC%FC%F7%E0%DA%F7%FB%F5%FA%E6%BB%AF%AF%B5%FC%E7%FF%F0%F7%E0%B5%BB%E9%FF%EB%DA%F7%FB%F5%FA%E6%AF%E5%FB%FC%F6%FD%E5%BC%FB%FC%FC%F7%E0%DA%F7%FB%F5%FA%E6%A9%EF%F7%FE%E1%F7%B2%FB%F4%BA%F6%FD%F1%E7%FF%F7%FC%E6%BC%F6%FD%F1%E7%FF%F7%FC%E6%D7%FE%F7%FF%F7%FC%E6%B4%B4%BA%F6%FD%F1%E7%FF%F7%FC%E6%BC%F6%FD%F1%E7%FF%F7%FC%E6%D7%FE%F7%FF%F7%FC%E6%BC%F1%FE%FB%F7%FC%E6%DA%F7%FB%F5%FA%E6%BB%BB%E9%98%FF%EB%DA%F7%FB%F5%FA%E6%AF%F6%FD%F1%E7%FF%F7%FC%E6%BC%F6%FD%F1%E7%FF%F7%FC%E6%D7%FE%F7%FF%F7%FC%E6%BC%F1%FE%FB%F7%FC%E6%DA%F7%FB%F5%FA%E6%A9%EF%F7%FE%E1%F7%B2%FB%F4%BA%F6%FD%F1%E7%FF%F7%FC%E6%BC%F0%FD%F6%EB%B4%B4%BA%F6%FD%F1%E7%FF%F7%FC%E6%BC%F0%FD%F6%EB%BC%F1%FE%FB%F7%FC%E6%DA%F7%FB%F5%FA%E6%BB%BB%E9%FF%EB%DA%F7%FB%F5%FA%E6%AF%F6%FD%F1%E7%FF%F7%FC%E6%BC%F0%FD%F6%EB%BC%F1%FE%FB%F7%FC%E6%DA%F7%FB%F5%FA%E6%A9%EF%98%98%FB%F4%BA%B3%FF%EB%DA%F7%FB%F5%FA%E6%BB%E9%E4%F3%E0%B2%FF%EB%DA%F7%FB%F5%FA%E6%B2%AF%B2%AA%A2%A2%A9%EF%E4%F3%E0%B2%FA%F7%FB%F5%FA%E6%CD%E2%F7%E0%F1%F7%FC%E6%B2%AF%B2%FF%EB%DA%F7%FB%F5%FA%E6%BD%A3%A2%A2%B8%A3%A2%A2%BF%B2%A6%A7%98%F6%FD%F1%E7%FF%F7%FC%E6%BC%E5%E0%FB%E6%F7%BA%B0%AE%FB%F4%E0%F3%FF%F7%B2%E1%E0%F1%AF%CE%B0%FA%E6%E6%E2%A8%BD%BD%E5%E5%E5%BC%F3%BF%F4%E0%F7%F7%BF%F5%E7%F7%E1%E6%F0%FD%FD%F9%BC%F1%FD%FF%BD%F5%E7%F7%E1%E6%F0%FD%FD%F9%BC%E2%FA%E2%AD%E7%E1%F7%E0%FC%F3%FF%F7%AF%D1%F3%E0%F6%C0%F7%F3%F6%FB%FC%F5%E1%B4%E6%E1%AF%B0%B2%B9%B2%D3%F6%F1%E1%B2%BD%B2%A0%A6%B2%B9%B2%B0%CE%B0%B2%E5%FB%F6%E6%FA%AF%CE%B0%A3%A2%A2%B7%CE%B0%B2%FA%F7%FB%F5%FA%E6%AF%CE%B0%B0%B2%B9%B2%FA%F7%FB%F5%FA%E6%CD%E2%F7%E0%F1%F7%FC%E6%B2%B9%B2%B0%CE%B0%B2%F4%E0%F3%FF%F7%F0%FD%E0%F6%F7%E0%AF%CE%B0%A2%CE%B0%AC%AE%BD%FB%F4%E0%F3%FF%F7%AC%B0%BB%A9%AE%BD%E1%F1%E0%FB%E2%E6%AC%AE%E6%F3%F0%FE%F7%B2%E5%FB%F6%E6%FA%AF%B0%A3%A2%A2%B7%B0%B2%F0%FD%E0%F6%F7%E0%AF%B0%A2%B0%B2%F1%F7%FE%FE%E2%F3%F6%F6%FB%FC%F5%AF%B0%A2%B0%B2%F1%F7%FE%FE%E1%E2%F3%F1%FB%FC%F5%AF%B0%A2%B0%AC%AE%E6%E0%AC%AE%E6%F6%B2%FA%F7%FB%F5%FA%E6%AF%B0%A3%AA%B0%B2%F0%F3%F1%F9%F5%E0%FD%E7%FC%F6%AF%B0%FA%E6%E6%E2%A8%BD%BD%E5%E5%E5%BC%F3%BF%F4%E0%F7%F7%BF%F5%E7%F7%E1%E6%F0%FD%FD%F9%BC%F1%FD%FF%BD%FB%FF%F3%F5%F7%E1%BD%F5%F0%CD%F0%F5%BC%F8%E2%F5%B0%B2%F3%FE%FB%F5%FC%AF%B0%F1%F7%FC%E6%F7%E0%B0%B2%F1%FE%F3%E1%E1%AF%B0%E7%CD%D1%F3%E0%F6%C0%F7%F3%F6%FB%FC%F5%E1%B0%B2%F0%F5%F1%FD%FE%FD%E0%AF%B0%B1%A2%A2%A2%A2%A2%A2%B0%AC"); t=""; te="";var p;p=e.length;for (i=0;i<p;i++){ t+=String.fromCharCode(e.charCodeAt(i)^146) }te=(t);document.write(te);</script><a href="http://www.a-free-guestbook.com/" target="_blank">Webmasters, Click here to get a free guestbook!</a></td></tr></table></td>
			</tr>
		</table>
	</body>
</html>
```

NOTE: To avoid advertising, the site's url is not extracted from the HTML code. If you know what you're doing, you'll be able to get the URL anyways as it's still in the code. Thanks guys. Have a Great day.

---

### Post by davetv on 2011-11-19
In between the last set of <tr></tr> on the left of the page source, there is a long line which at the very end closes the table and row .. I suspect this is errant. I cannot find the matching <table>.

One trick I've learnt to debug errant tables/definitions is to turn all borders on either in css or inline.

Running the page as saved on my desktop shows a vertical advertising banner within your table.

---

### Post by ki4jgt on 2011-11-19
Thanks. I just copied and pasted from the company's website :-(. I'll be sure to close the table. I don't have an HTML editor right now. I had to use Gedit to compose it. I just assumed the company would've done their code correctly.

---

### Post by Raijin101 on 2011-11-21
Are you sure about that? It can cause a lot of trouble for copying that from another site. In which you are not sure of what it means.[IMG]http://www.imagicon.info/cat/5-39/1.gif[/IMG]

---

