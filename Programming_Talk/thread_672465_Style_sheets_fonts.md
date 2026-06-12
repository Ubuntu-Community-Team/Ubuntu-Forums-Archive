---
title: "Style sheets fonts"
date: 2008-01-19
forum: Programming Talk
---

### Post by beerguzzler on 2008-01-19
Hello all,

I'm in the process of switching to Ubuntu from XP.

I have my own [site]("http://www.jadrallypix.me.uk") that uses CSS sheet.

The site has w3c ticks for both HTML and CSS and the formatting of the fonts is fine in FIrefox/Opera/Safari/IE in WIndows.

However, in both FIrefox and Opera within Ubuntu, the fonts are not displaying correctly.

Is there something extra I need to insert in the style sheet, or is it a Linux Browser issue?

Any help or pointers to other threads very welcome.

Thanks.

---

### Post by LaRoza on 2008-01-19
Looks fine to me.

Opera 9.50b, Ubuntu 7.10

---

### Post by beerguzzler on 2008-01-19
Forgot to mention that the h1 font is meant to be Monotype Corsiva, but seems to be displaying normal to me

---

### Post by LaRoza on 2008-01-19
> **beerguzzler said:**
> Forgot to mention that the h1 font is meant to be Monotype Corsiva, but seems to be displaying normal to me
```

body, td, th {
	margin-top: 0.1cm;
	background-color: #cddcf0;
	font-family:"Times New Roman", Times, serif;
	font-size:16px;	
	color: #000000;
}
A:link {text-decoration: none; color: #000080;}
A:visited {text-decoration: none; color: #000080;}
A:active {text-decoration: none; color: #000080;}
A:hover {text-decoration: none; color: #000080;
}	
h1 {
	font-family: "Monotype Corsiva";
	font-size:36px;
	color: #000080;
}

```

(Snippet of the style sheet)

If that font is not installed, the browser uses the default font. You should use "serif", "sans-serif", "monotype", or "fantasy" after any font-family declaration so the browser can find a suitable font. 

Also, links should be underlined. I didn't realize some of the text on the page were links. It is not a good idea to mess with what the user expects.

---

### Post by beerguzzler on 2008-01-19
Thanks for your help. :)

---

