---
title: "javascript problem??"
date: 2011-06-04
forum: Programming Talk
---

### Post by scott_tiger on 2011-06-04
<script type="text/javascript">
function agree()
{
if (document.all||document.getElementById){
          for (i=0;i<theform.length;i++){
          var tempobj=theform.elements[i]
    if(tempobj.type.toLowerCase()=="submit"||tempobj.type.toLowerCase()=="reset")
//disable em
                tempobj.disabled=true
                }
                }
}
</script>
                
i used the above script to submit the form once,but it didn't worked... Help Required??

The script actually should disable the submit and reset button it is not doing that.

---

### Post by epicoder on 2011-06-04
Please use CODE tags to post your code. [ CODE]code[ /CODE]
I noticed a couple problems in your script, most having to do with variables.

The one I noticed first is that you never define the variable "theform". The script will still work if you define it in the same <script> element outside of a function, but I find it's easier to figure out what the script does later if you define all variables inside of a function, or if you pass a script level one as an argument. You could also use the keyword 'this' in onsubmit in the form element:
```
<script type="text/javascript">
function agree(theform) {
...
<form onsubmit="agree(this)" >
```Another problem that I noticed is the first line inside of your for loop.
```
var tempobj=theform.elements[i]
```The problem is that you are declaring tempobj each time you go through the loop. I don't know if JS allows this, but even if it does, it's bad coding practice. You should only declare a variable once. Here's how you should structure it:
```
var tempobj
for (i=0;i<theform.length;i++){
  tempobj=theform.elements[i]
```The last problem I noticed is a syntax error. This line is missing a { and has a couple extra spaces.
```
if(tempobj.type.toLowerCase()=="submit"||tempobj.t  ype.toLowerCase()=="reset") //There should be a { where this comment is.
//                                                ^ There shouldn't be a space here
```Also, your code could use some indentation and whitespace. It isn't necessary, but it makes it a lot easier for others to read your code.

---

### Post by scott_tiger on 2011-06-05
Thanx..4 ur reply but the problem still persists....

---

### Post by epicoder on 2011-06-05
It's probably no consolation to you, but your script with my fixes works fine here. Check that you are passing the correct element (the form itself, not the buttons) to the script, and make sure that your function definition is in a script element that is in the head, not the body. Also make sure that if you are using the onsubmit attribute, it is in the form element, not the submit button. onclick on the submit button won't work with "this" either. 

Check your browser's error console (Firefox > Web Developer > Web console in firefox) for any errors output by the JS engine and post them here if there are any. Good luck.

---

