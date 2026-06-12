---
title: "Do you know HTML? Then maybe you can make faroese homebanking Linux compatible."
date: 2006-11-27
forum: Programming Talk
---

### Post by Sammi on 2006-11-27
[http://en.wikipedia.org/wiki/Faroe_islands]("http://http://en.wikipedia.org/wiki/Faroe_islands") <- small group of islands between Iceland and Scotland.

PLEASE HELP ME! No faroese bank has a completely Linux compatible homabanking system, as they are in fact all delivered by the same company, which is very Microsoft oriented. ](*,)

Well actually the only thing that's not working at all, is transactions, and this is because the "OK" button on the transactions page on the homebanking homepage does nothing under Linux/Firefox, while it works fine in Windows/Explorer.

This might actually be good news, as the solution may be very easy(fingers crossed). On another forum somone remarked that the page might not be W3C compliant and lacking closing tags, which Explorer wrongfully accepts, and Firefox doesn't, but this person didn't help me further.

Please help me by looking through the HTML code for mistakes, that I can submit to the company providing this crappy service.

This is the HTML code of the frame with the non-functioning "OK" button:```
<HTML> 
<HEAD> 
<META name="GENERATOR" content="Microsoft Visual Studio 6.0"> 
<LINK rel="stylesheet" type="text/css" href="../includes/Stylesheets/NetBank.css"> 
<SCRIPT Language="JavaScript" SRC="../includes/javascript/pages.js"></SCRIPT> 
<TITLE>eToll</TITLE> 
</HEAD> 
<BODY> 
   <TABLE width="100%" height="100%" class="backgroundBottom" border="0" cellspacing="0" cellpadding="0"> 
      <TR> 
         <TD valign="center" align="right">             
            <INPUT class="button" type="button" value="Angra" name="CANCEL" id="CANCEL" onclick="javascript:changePage('../accounts/accountMain');"> 
 
            <INPUT class="button" type="button" value="OK" name="ok" id="ok" onclick="javascript:javascript:submitPayment();"> 
         </TD> 
      </TR> 
   </TABLE> 
</BODY> 
</HTML>
```Anyone find any mistakes. Missing closing tags, maybe??

---

### Post by Tomosaur on 2006-11-27
This may be a simple case of removing the duplicate 'javascript' text from this line (I bolded the bit possibly causing the problems):

<INPUT class="button" type="button" value="OK" name="ok" id="ok" onclick="**javascript:**javascript:submitPayment();">

Hopefully by removing that, other browsers won't get confused.

---

### Post by Sammi on 2006-11-28
Thanks for the suggestion :D

I almost hope it's not that pitifully easy... for their sake, so they can keep face :p

---

### Post by ohgod on 2006-11-29
If you're using Firefox, you might want to check out the Error Console after trying to click that button (Tools->Error Console).  If it's a javascript error, it'll show up there.

I ran this through the W3C html validator, and sure enough it's not valid.  Though that might have nothing to do with your problem.

---

### Post by mssever on 2006-11-29
I hope your bank is more responsive than the companies I've dealt with in this regard. My ISP has a download speed testing website. It only works in IE because of an extremely simple bug: they put "void" before a function definition. I've contacted them several times and given them the fix, but they just told me that they only support IE.

My bank's website has a Javascript bug in one section that's apparently due  to using some third party JS library. If only the devs would drop the library and test in Firefox, everything would be fine. The JS would be trivial to implement without a lib, and there would be less bloat and less to go wrong. But, they tell me that they only support IE.

You might point out that Firefox is the number 2 browser, so it makes sense to support it. Also, what about their customers who don't use Windows (MacOS, Linux)? IE is only available for Windows. It used to be available for MacOS, but MS dropped support for MacOS years ago.

---

### Post by jatos on 2006-11-29
People like that need to be shot. In case they hadn't noticed, FireFox is now in mainstream use, and can easily be supported. Do you think if enough us bugged these places they might actually do something about it?

---

### Post by mssever on 2006-11-29
> **jatos said:**
> People like that need to be shot. In case they hadn't noticed, FireFox is now in mainstream use, and can easily be supported. Do you think if enough us bugged these places they might actually do something about it?

Maybe, although taking our business elsewhere might be the only thing that gets their attention. In the case of my ISP, I can't switch companies unless I want to return to dialup or pay twice what I'm paying now. So, I'm stuck. (I live in a rural area without many alternatives.)

---

### Post by Sammi on 2006-12-01
> **mssever said:**
> I hope your bank is more responsive than the companies I've dealt with in this regard.
 I sent Tomosaur's suggested fix three day ago, but surely enough they haven't responded yet :roll:

---

