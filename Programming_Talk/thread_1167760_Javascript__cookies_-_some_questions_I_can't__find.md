---
title: "Javascript  cookies - some questions I can't  find after searching"
date: 2009-05-23
forum: Programming Talk
---

### Post by Ubu2010 on 2009-05-23
Hi all,

I am fairly decent at Javascript basics, but I can't seem to find any solid information on how to incorporate cookies into an HTML document. I have even searched Ubuntuforums.org, and I still can't seem to find the answers to a couple questions.

1. If I were to use the code below, how would I actually create, read, and erase the cookie using the functions below? In other words, what would be a good way for me to see the results of how the cookies is created and displayed afterwards when it is read ? Which leads to question # 2 ...

2. Could I just make a document.write for the readCookie function to show the visitor's last visit ? 

Could I use a document.write and have it display on the page, like the last time I visited the page ? I just need to know how to make these or some similar functions work, so I can see the results of the code at work. 

All I can ever find is how to make the functions, and what it all means, but no way to see it on a page I create. Any ideas ? I know there are tutorials, but none that I can find that shows how to make it part of a web page, like to display a last visited time and day, for example.

Thank you in advance if anyone can help !

I found this code here  [http://www.quirksmode.org/js/cookies.html]("http://www.quirksmode.org/js/cookies.html") :

```
function createCookie(name,value,days) {
	if (days) {
		var date = new Date();
		date.setTime(date.getTime()+(days*24*60*60*1000));
		var expires = "; expires="+date.toGMTString();
	}
	else var expires = "";
	document.cookie = name+"="+value+expires+"; path=/";
}

function readCookie(name) {
	var nameEQ = name + "=";
	var ca = document.cookie.split(';');
	for(var i=0;i < ca.length;i++) {
		var c = ca[i];
		while (c.charAt(0)==' ') c = c.substring(1,c.length);
		if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
	}
	return null;
}

function eraseCookie(name) {
	createCookie(name,"",-1);
}
```

---

### Post by mdgrech on 2009-05-23
Honestly I would say you should use a server side technology such as PHP to place cookies.  Using your method if the user has Javascript turned off the cookie will never happen.

---

### Post by Ubu2010 on 2009-05-23
Thank you for your response, mdgrech. Well, to tell you the truth, I have been trying really hard to get the concept on how to code cookies in Javascript, because I know it is supposed to be an easy concept, yet it is kicking my butt! It's just a personal thing, I hate not knowing how to do something code-wise once I set my mind to it. 

Regarding your answer though, that seems like a very legitimate point, regarding placing the cookies on the server in case a user doesn't have cookies turned on. Well, for now I will give up the Javascript/cookies thing, I have been trying like for a week to figure it out, visiting tutorial sites, etc. Maybe some day I will get it, not the end of the world if I don't. But thanks again !

---

