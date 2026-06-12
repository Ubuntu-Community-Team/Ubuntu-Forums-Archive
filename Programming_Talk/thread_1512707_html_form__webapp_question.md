---
title: "html form / webapp question"
date: 2010-06-18
forum: Programming Talk
---

### Post by badperson on 2010-06-18
Hi,
dumb webapp question. 
I want to create an html form in an app I'm writing, very much like the form I'm using to submit this question. For example, if I type some text, then highlight that text: 

> that text

and hit the "quote" icon, the text is then wrapped in QUOTE /QUOTE
tags. What is it that modifies that text...there's not http request involved there, is there? Is it javascript? sorry for  the newb question. 

bp

---

### Post by martijntje on 2010-06-18
Yes. This is done with javascript. It is of course possible to do this server-side too, but javascript is much faster in this case.

---

### Post by badperson on 2010-06-18
that's one of those questions I was %98 sure of before I finished typing the question... ::lolflag:

anyway, I have a form I'm working on, and I have this input:

```
	
<input type="image" onclick="document.getElementById('sampleText').value = tagHeading(document.getElementById('SampleText'))" value="tag data" src="Bubble 3.gif" alt="create tag"/>

```

when the type is set to "button" the code works properly, but when set to image it doesn't, it erases anything in the text area. 

is is changing from onclick to something else?
bp

---

### Post by myrtle1908 on 2010-06-18
Best not to mix HTML and JS.  Try this (although it doesn't really answer the question as to why yours doesn't work) ...

```
<script>
window.onload = function() {
  var myImg = document.getElementById('myImg');
  myImg.onclick = function() {
    var myTextArea = document.getElementById('myTextArea');
    myTextArea.value = 'Something';
  };
};
</script>

<img id="myImg" src="bubble3.gif" style="cursor:pointer"/>
<textarea id="myTextArea">
</textarea>

```

Also, you should use Firebug to help debug your code.

[http://www.getfirebug.com](http://www.getfirebug.com)

Good Luck.

---

### Post by badperson on 2010-06-18
thanks, 
I got that to work ok. Couple questions:
[LIST]
[*]the "function()", is that an arbitrary name, could you have said "function1() and function()2, or is what you have standard for an anonymously declared function?
[*]is it good or bad to have multiple functions inside one <script></script> node?
[/LIST]


thanks!
bp

---

### Post by myrtle1908 on 2010-06-18
> **badperson said:**
> 
[*]the "function()", is that an arbitrary name, could you have said "function1() and function()2, or is what you have standard for an anonymously declared function?


No, it is not an arbitrary name.  We are assigning an anonymous function as the onclick handler.

> **badperson said:**
> 
[*]is it good or bad to have multiple functions inside one <script></script> node?


Perfectly fine.  For large projects, I keep my JS code in multiple files which are concatenated, obsfucated and compressed at delivery time.

---

### Post by Krupski on 2010-06-19
> **myrtle1908 said:**
> 
Also, you should use Firebug to help debug your code.

[http://www.getfirebug.com](http://www.getfirebug.com)

Good Luck.

Oh yes... a BIG +1 on that suggestion.

For web development, I would be blind without Firebug.

(note to everyone Firebug is for Firefox, not MSIE).

---

### Post by Krupski on 2010-06-19
> **myrtle1908 said:**
> I keep my JS code in multiple files which are concatenated, obfuscated and compressed at delivery time.

See: [http://jsbeautifier.org/](http://jsbeautifier.org/)

It cleans up those hideous single line and obfuscated monsters.

---

### Post by myrtle1908 on 2010-06-19
> **Krupski said:**
> See: [http://jsbeautifier.org/](http://jsbeautifier.org/)

It cleans up those hideous single line and obfuscated monsters.

No.  I'm talking about when the code is delivered to the client (web browser).  When you have large JS projects (~900kb), supporting many widgets and layouts, it is best to compress/obsfucate upon delivery.  Check out GZip compression and Crockford's or YUI compressor.

Later edit: as an aside, I use jsbeautifier code in our core system to format the JSON sent between client and server when in debug/diags mode.

---

### Post by badperson on 2010-07-01
thanks for the replies. I'm trying to write a form that has a text input area, I want the image icon to tag the select text; changing "text" to "[heading]text[/text]" or something. Here's the code:

```
<html><head><title>Sample JavaScript Input Form</title>

<!-- java script -->



<script>

window.onload = function() {

  var myImg = document.getElementById('myImg');

  myImg.onclick = function() {

    var textInput = document.getElementById('textInput');

	//alert('text input is: ' + textInput.value);

    var selText = getSelectedText();

	//alert('selected text: ' + selText);

    textInput.value = tagText(selText, 'test');

  };

};



	function tagText(text, tagname){



		var selectedText = getSelectedText();

		

		var taggedText = '<tag>' + selectedText + '</tag>';

		var newText = text.replace(selectedText, taggedText);
		return newText;

	}

	



	function getSelectedText(){



		var text = '';



			if(window.getSelection){

				text = window.getSelection();

			} else if(document.getSelection){

				text = document.getSelection();



			} else if (document.selection){

				text = document.selection.createRange().text;

			} else {

			text = 'problem';

			}

			alert ('in get selected text function, text is: ' + text);

			return text;



	}	

</script>



</head>

<body style="background-color:#600000;color:#E8E8E8;font-family:verdana;margin-left:40px;margin-right:40px">

<h1 style="text-align:center">Sample Javascript Input Form</h1>



<form>

	<h2>Enter your data here:</h2>

	<img id="myImg" src="testIcon.gif" style="cursor:pointer" alt="click the bowl of love to tag your text"/><br/>

	<textarea id="textInput" cols="100" rows="20"></textarea>

	<br/>

	

</form>







</body></html>
```

the getSelectedText function seems to have trouble returning a value.
bp

---

### Post by myrtle1908 on 2010-07-01
Not tested in IE ...

```
window.onload = function() {
  var myImg = document.getElementById('myImg');
  myImg.onclick = function() {
    var textInput = document.getElementById('textInput');
    var selStart = textInput.selectionStart;
    var selEnd = textInput.selectionEnd;
    var v, sel, start, end;
    if ((selEnd - selStart) > 0) {
        v = textInput.value;
        sel = v.substring(selStart, selEnd);
        sel = '<tag>' + sel + '</tag>';
        start = v.substring(0, selStart);
        end = v.substring(selEnd, v.length);
        textInput.value = start + sel + end;
    }
  };
};
```

You should be able to figure it out from here.  Better yet use one of the many web based WYSIWYG editors out there like TinyMCE or CKEditor.

---

### Post by badperson on 2010-07-02
awesome...that worked. I changed it around a bit, and got this to work with no firebug warnings...

```
<script>

window.onload = function() {

  var myImg = document.getElementById('myImg');

  myImg.onclick = function() {

    var textInput = document.getElementById('textInput');

    var selText = tagSelectedText('textInput', 'tag');

  };

};




	function tagSelectedText(id, tag){
	var text = document.getElementById(id);
	var selectionStart = document.getElementById(id).selectionStart;
	var selectionEnd = document.getElementById(id).selectionEnd;
	var v, sel, start, end;
		if((selectionEnd - selectionStart) > 0){
		v = document.getElementById(id).value;
		sel = v.substring(selectionStart, selectionEnd);
		sel = '<' + tag + '>' + sel + '</ ' + tag + '>';
		start = v.substring(0, selectionStart);
		end = v.substring(selectionEnd, v.length);
		document.getElementById(id).value = start + sel + end;
		}
	}





</script>
```

---

### Post by badperson on 2010-07-02
works in firefox and chrome....not IE.
bp

---

### Post by myrtle1908 on 2010-07-02
> **badperson said:**
> works in firefox and chrome....not IE.
bp

IE is a pain

```
var normSelected = function(ta) {
  if (document.selection) {
    var bk = document.selection.createRange().getBookmark();
    var sel = ta.createTextRange();
    sel.moveToBookmark(bk);
    var left = ta.createTextRange();
    left.collapse(true);
    left.setEndPoint("EndToStart", sel);
    ta.selectionStart = left.text.length;
    ta.selectionEnd = left.text.length + sel.text.length;
  }
};

window.onload = function() {
  var myImg = document.getElementById('myImg');
  myImg.onclick = function() {
    var textInput = document.getElementById('textInput');
    normSelected(textInput); // normalise
    var selStart = textInput.selectionStart;
    var selEnd = textInput.selectionEnd;
    var v, sel, start, end;
    if ((selEnd - selStart) > 0) {
        v = textInput.value;
        sel = v.substring(selStart, selEnd);
        sel = '<tag>' + sel + '</tag>';
        start = v.substring(0, selStart);
        end = v.substring(selEnd, v.length);
        textInput.value = start + sel + end;
    }
  };
};
```

---

