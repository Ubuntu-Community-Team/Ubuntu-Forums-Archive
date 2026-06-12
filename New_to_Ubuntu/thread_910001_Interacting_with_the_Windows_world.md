---
title: "Interacting with the Windows world"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by japhyr on 2008-09-04
Hello everyone,

I made a straight ubuntu installation on my computer in June, and have been using it happily since then.  However, the new semester has just begun and tomorrow I will begin emailing papers to professors on a regular basis.  I have a couple questions as I begin to send open office documents to people who probably use ms office, people who have power over me. :)

[LIST]
[*]Do I just save my .odt file as word 97/2000/XP (.doc) and email it as an attachment?[*]If I do this, and the professor makes comments with "track changes" on, will I see those comments?  Or will I lose the track changes formatting when I open the returned word version?[*]Is there anything I should do to make sure I am not sending a virus with my attachment?
[/LIST]

---

### Post by iaculallad on 2008-09-04
First question: Yes, you could just send it as M$ Word format.
Second Question: I have not tested opening commented works on M$ word on OO.
Third Question: No need to worry about you sending virus on attachments since virus "does not" really thrive well in Linux.

---

### Post by fatality_uk on 2008-09-04
There are occasionally some issues with OOo exports to *.doc. This isn't the fault of OOo, but a lack of clear information from Microsoft re file formats. On the whole, I would say you are likely to not run into any major issues.

Tracking changes works very well.

As for Viruses, you could install something like AVG for Linux before sending a file

---

### Post by ivikas on 2008-09-04
Helo Japhyr,

                First of all you know the fact,microsoft word format are used widely.So does you mean to say your professor have windows machine.So, all you have to open your openoffice created document(if any) and take the "save as" option from  the file menu.This will open a new window, on the name field give the name you want to save and on the right bottom corner select the file type as "Microsoft Word 97/2000/xp(doc)" and save it and you are done.If it is a regular text,your professor will get it right at the other end.If he is sending some text based comments,it will also be visible to you.If he is sending some windows only grapgics,animations, chances are "MAYBE" you can read it.

If you want to save all the document you create in doc(MS WORD) format by default do the following:

1.From "Tools" menu select "options",this will open up "options"  window.

2.In the left pane of the "options" window you will find  "+Load/Save"(Click on the plus(+)sign beside it.

3.From the suboption that opens in left pane select "General"

4.In the right side you will see at the bottom of window

   Document type                            Always save as
   Text document(by default)                [COLOR="Red"]ODF Text Document[/COLOR]
5.Now click on [COLOR="Red"]ODF Text Document[/COLOR] and select as [COLOR="Red"]Microsoft Word 97/200/XP[/COLOR] and click the OK button and you are done.

       Again when you create a fresh document  in Linux you need not be feared about virus so the file you sending to your professor will be clean.And linux is less prone to virus than windows.If any way you want to install antivirus to scan all incoming files from internet or thoose files that are on windows partitions you can use

clam or f-prot(sorry don't have link now,just google it)

---

### Post by jemate18 on 2008-09-04
> **japhyr said:**
> Hello everyone,

I made a straight ubuntu installation on my computer in June, and have been using it happily since then.  However, the new semester has just begun and tomorrow I will begin emailing papers to professors on a regular basis.  I have a couple questions as I begin to send open office documents to people who probably use ms office, people who have power over me. :)

[LIST]
[*]Do I just save my .odt file as word 97/2000/XP (.doc) and email it as an attachment?[*]If I do this, and the professor makes comments with "track changes" on, will I see those comments?  Or will I lose the track changes formatting when I open the returned word version?[*]Is there anything I should do to make sure I am not sending a virus with my attachment?
[/LIST]

For your first
> Yes for the M$ Office to read your documents you have to save it as 97/2000/XP -> Though sometimes the formatting changes or is not what you have in your native linux

For your second
> Can't track changes......Personally not tested

For your third
Linux is LINUX and it is not
[COLOR="DarkGreen"]V[/COLOR]irus
[COLOR="Red"]I[/COLOR]ntrusion
[COLOR="Purple"][COLOR="Navy"]S[/COLOR]pyware
T[/COLOR]rojan
[COLOR="DarkOrange"]A[/COLOR]dware

And does not have any of those above

---

### Post by Sef on 2008-09-04
> Linux is LINUX and it is not
Virus
Intrusion
Spyware
Trojan
Adware

And does not have any of those above

If you have an email client, then an anti-virus is best.  Malware can ride of top of GNU/Linux, and infect your Windows using friends.  Otherwise no virus protection is needed.

---

### Post by japhyr on 2008-09-04
Thanks for all the replies.  I have a couple followup questions on the formatting question and one on viruses.

[LIST=1]
[*]When I save an odt document in .doc format, it says I may lose some formatting.  If I go ahead and save in .doc format, then open that .doc file, will I see any of those formatting changes that Word users will see?
[*]Are there particular kinds of formatting that don't get translated accurately, like tables or something?
[*]Regarding viruses, I know my system is quite safe.  This is what I was thinking of:> If you have an email client, then an anti-virus is best. Malware can ride of top of GNU/Linux, and infect your Windows using friends. Otherwise no virus protection is needed.It seems like many linux users, probably most new linux users, ignore this.  Is that lazy or irresponsible, or is a windows user who gets a virus from one of us likely to get it from somewhere if they're vulnerable in the first place?  I guess it's also a matter of me not wanting my messages and attachments rejected by a windows recipient because I'm carrying a virus.  All that said, what is a good linux-end antivirus just for the purpose of checking emails and attachments before they are sent out?
[/LIST]

---

### Post by OldTimeTech on 2008-09-04
There is an AVG for Linux....the one in the repositories is ClamAV...either will work well.

---

### Post by knattlhuber on 2008-09-04
I work as a medical researcher and I use OOo at work. I often get manuscripts from Word users with tracked changes and I haven't had any major incompatibility issues. I never noticed what formatting actually gets lost when you save an .odt as .doc. The different fonts for Linux and Windows sometimes make tables look funny because the Linux font used by OOo may take up more space in a cell than its Windows counterpart. Nothing serious though. Also, remember that even different MS Word versions are sometimes not compatible with each other.

There's one caveat: From my experience, .rtf files may give you headaches in OOo. I had one (rtf file, NOT headache) recently where a colleague had highlighted text and when I opened it in OOo there was no highlighting at all.

HTH

---

