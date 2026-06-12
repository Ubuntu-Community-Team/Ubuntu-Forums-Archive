---
title: "[xhtml + css] text in div or p not going to next line"
date: 2009-02-14
forum: Programming Talk
---

### Post by TreeFinger on 2009-02-14
i have some content text i am trying to print and instead of going to the next line, the text continues running horizontally. 

here are some snippets of code.

xhtml:
[php]
<!-- ENDING HORIZONTAL NAV -->
	</div>



	<!-- NOTE SURE IF THIS IS A GOOD IDEA BUT OPENING 'CONTENT' DIV -->
	<div id="index_0-0"> 

	
	hahsefkawtujhawjfnjsanbdvifasigffkjnsalfknaosihgfo;asgfo

	
	
	<!-- CLOSING ID_0-0 -->i
	</div>

	<div id="index_0-1"> 

	
	hahsefkawtujhawjfnjsanbdvifasigffkjnsalfknaosihgfo;asgfo

	
	
	<!-- CLOSING ID_0-1 -->
	</div>
	<!-- FOOTER -->
[/php]

css:
[php]
div#index_0-0 {

padding:2px 2px;
margin:2px 2px;
float:left;
width:281px;

}
div#index_0-1 {

margin:2px 2px;
padding:2px 2px;
float:right;
width:281px;
}
[/php]

---

### Post by Reiger on 2009-02-14
Because you use float. ;)
The simple way is to add a <br />.

---

### Post by TreeFinger on 2009-02-14
> **Reiger said:**
> Because you use float. ;)
The simple way is to add a <br />.

how should i do it then?

by pixel?

---

### Post by Reiger on 2009-02-14
No float is fine by any means, but because it was originally designed with just images in mind (or so I read somewhere, anyway) it has the side effect of turning a block element into an inline element. Thus why your divs align alongside each other without line break (news paper column style, so to speak); hence you need the br.

I think this should do it:
<div>
<div style="float:left;">Whee, I believe I can fly!</div><br />
<div style="float:right;">Float to the right.</div></div>

---

### Post by Peter76 on 2009-02-15
You should not use breaks here, if you want content to start on a new line after a float, use ```
clear: left;
``` in your css for index0-1, or ```
clear: right;
``` for the other way around.
But why are you using floats here in the first place? What are you trying to do?

Hope this helps a bit

---

