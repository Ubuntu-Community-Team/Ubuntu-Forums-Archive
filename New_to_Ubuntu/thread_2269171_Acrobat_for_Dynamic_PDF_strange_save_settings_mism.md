---
title: "Acrobat for Dynamic PDF: strange save settings mismatch"
date: 2015-03-13
forum: New to Ubuntu
---

### Post by harelb on 2015-03-13
Hi, this is a follow-up to my earlier question, which I think is solved, this one:

[Software to edit/use Interactive (or "Dynamic"?) PDF]("http://ubuntuforums.org/showthread.php?t=2264061&page=2&p=13223514#post13223514")

I think I have a working version of Acrobat now on my ubuntu, so be able to fill out that form..it's an important legally related document so once I click "start" I may want to save things (it might not let me "go back and change previous answers") to the interactive/dymaic ("your answer to question 4 affects what you do or don't see in question 5" type of thing, is my understanding) so I want so save previos stages as I go along..and am about to do so, but in the Instructions (a separate PDF file that is plain simple PDF) I found this:

> 
 Some versions of Adobe Acrobat/Reader give you the option to 'Save a Copy'. DO NOT DO THIS, as it will remove certain functionality from within the form. If you need to save this form to another location after opening it then **you must use 'Save As...' in Adobe Acrobat/Reader's file menu.**"

The above threw me off because my File menu has** "Save a copy..." and "Save as text..." **and "Attach as email.." among others ("Print", "Reload", "Open", "Collaborate" which has sub-menus to upload and more, "Create PDF using acrobat.com") but* the only two saving related ones are "Save a copy" and "Save as text" *- neither sounds right (I dont' want to save plain-text obviously) and neither one is "Save As") 

Anyone know what's the story here? Especially if you have experience with these dyanamic/interactive PDF things on linux...or if you don't have experience (or good reason to believe) that the File menu would be deliberately different (why Adobe possibly want to do that?) and most of all, which is the path forward for savings, that is the "safe" way, keeping in mind the above quoted Instructions I have?

---

### Post by monkeybrain20122 on 2015-03-14
Can you actually provide a link to the document? Running pdf-xchange-viewer in wine probably works. It works for all sorts of interactive forms and is very light, not like Adobe.

---

### Post by harelb on 2015-03-15
Hi,
I'm not sure if I'm allowed to share the document...but I woudl be surprised if the File menu changes depending on which document one uses..? So maybe you mean (hopefully you mean) a screenshot of the behavior, which I am including. As you can see from the screenshot, the File menu for Adobe Reader 9 on on my (ubuntu) system.

As you can see, with my mouse is on the Collaborate entry on the File menu, the next two entries right below it are "Save a copy.." and "Save as text.." neither says "Save as.." but the directions say:
> 
Note 1: Some versions of Adobe Acrobat/Reader give you the option to 'Save a
Copy'. DO NOT DO THIS, as it will remove certain functionality from within the
form. If you need to save this form to another location after opening it then you must
use 'Save As...' in Adobe Acrobat/Reader's file menu

I could experiment to see if "Save as text" will allow me to save as something else (by changing the .txt default in there with a .pdf or something...it would still be a VERY strange and poor choice of File menu entry to call it "Save as text.." don't you think?) and I'd rather avoid that kind of experimentation, if possible, hoping someone with experience with Reader (or Reader 9) on ubuntu, plus this Screenshot, or others just from this Screenshot, versus the quoted instructions, can share their expertise/thoughts?

[ATTACH=CONFIG]260626[/ATTACH]

---

### Post by monkeybrain20122 on 2015-03-15
In the thread you linked to you said 

> I need to fill out some kind of interactive  PDF. "Interactive" means that, depending on how you answer one question,  the next question/fill-in you get, will be different. The contact  person for where I got this, thinks (but seems not 100% sure) that this  sub-type of the PDF form, is called, **Dynamic PDF**

Like I said I have never needed adobe, I have filled forms like that with PDF-Xchange-viewer running in Wine but without the actual form I obviously cannot tell whether it works in your case.

---

### Post by harelb on 2015-03-15
Somehow "PDF-Xchange-viewer" didn't sound like the name of a windows program, but a google confirms that it is...last time I used wine was 18+ months ago...not sure how on my old 2007 or so PC this will work...

but if nothing else works (I did take all the trouble to find and download and get Acrobat Reader 9 to work on my linux...so I'd prefer to stick with it...my quetsion, after all, is merely about the strange name discrepancy; the PDF reader works as a reader.I'm trying to just merely get clarification from someon (there must be at least **one** on all of ubuntu forums.org) who has used Acrobat REadfer on Ubuntu and tell me the ansewr to the simple question:* is that File menu the normal one one is supposed to see? and if so what about "save as.."*?) then I'll certainly look into pdf-xchange-viewer..

---

