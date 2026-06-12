---
title: "HOWTO: resolve SWT error in Aptana running on Hardy"
date: 2008-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by MikeEvans on 2008-08-06
**UPDATE: Thanks EddieA for providing the proper fix for this error**

**Symptoms:**
[LIST]
[*]You get an "An SWT error has occured." when doing various things in Aptana Studio
[*]You can't update Aptana, view new messages, or preview code
[*]Your running Firefox 3 (default on Hardy)
[/LIST]

**Cause:**
[INDENT]Aptana integrates with Firefox 2 only.  The errors relate to it not finding some needed libraries[/INDENT]

**Resolution 1 (recommended):**
[INDENT]Follow the official install instructions. This will get Aptana working with your current version of Firefox. [http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux]("http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux")[/INDENT]

**Resolution 2:**
[INDENT]Install firefox 2.  Note that this will NOT cause any issues with Firefox 3 usage.  It is safe to have them both installed.  Run the following code and restart Aptana.  Everything should work fine.
```
sudo apt-get install firefox-2
```[/INDENT]

**Sources:**
[INDENT]Resolution found here: [http://support.aptana.com/asap/browse/STU-1533;jsessionid=4938CAE92B64BDB89EA29D851BDCC779?page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel]("http://support.aptana.com/asap/browse/STU-1533;jsessionid=4938CAE92B64BDB89EA29D851BDCC779?page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel")[/INDENT]

---

### Post by mooncaptain on 2008-09-20
Holy IDE batman that really worked!

---

### Post by EddieA on 2008-10-30
Although this 'seems' to work (it was what I did too) it means that the browser in your preview window is not FF3 but FF2 which means  at least that your CSS will not display properly if you are writing for FF3 as , of course, FF2 is not as CSS compliant.
I still don't know how to fix this properly.
Eddie

---

### Post by EddieA on 2008-10-31
Here's the real fix:
[http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux]("http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux")

Cheers 
Eddie

---

### Post by susanpenter on 2008-11-06
Hi I am not very confident when it comes to using the terminal so could someone give my a breakdown of how to do this:

Instead you need to install XULRunner and create a startup script called, say, runAptana.sh in /usr/local/aptana

I have XULRunner installed but my Aptana is downloaded to /home/susan/Downloads/Aptana/aptana it launches but then I get the SWT error straight away.
I think I need to do the startup script now.
Thanks,
Susan

---

### Post by EddieA on 2008-11-06
Hi Susan
You may have a different problem if you are getting swt error straight away.
If you are getting it when you try to preview your code in th FF3 browser here is the fix (in plain English  :)   )

Using your favourite file explorer:
find your XUL runner directory - make a note of the full path name
find your aptana (i.e where it is installed) directory ditto pathname
these paths are the  two lines you need to customize the script for your setup.

create a plain text document and paste the two lines below into it:



> export MOZILLA_FIVE_HOME=/usr/lib/xulrunner 
/home/susan/Downloads/Aptana/aptana

(NB substitute YOUR xulrunner directory in the first line )
then save it in your aptana directory as runAptana
again, using your file browser, navigate to 'runAptana', which is now your launch script, right-click choose 'properties' then 'permissions', and check 'allow executing file as program' 
If you click on the file it should then open Aptana.
Also modify any launchers or menu item to point to yout new 'runAptana' script.
Hope it works
Eddie

---

### Post by susanpenter on 2008-11-06
Thanks Eddie, I fear mine may be a seperate error though because it appears as soon as I launch Aptana and then I have to close it straight away without using it at all.

I tried following your instructions above but Aptana didn't even begin to launch from the created file.  This time when I launched it with the original launcher when it asked me whether I wanted to close Aptana I have said no and asked it to download updates so I will have to watch this space and see if it works.

---

### Post by EddieA on 2008-11-06
That's strange - it should launch.
I omitted the name of the Aptana file (i.e the actual program file) which I believe is AptanaStudio (as capitalized). if your directory is:
/home/susan/Downloads/Aptana/aptana 
please go to that directory and check that's where AptanaStudio is.
then the second line  should read
/home/susan/Downloads/Aptana/aptana/AptanaStudio


if that doesn't work then post all your script here and let's have a look.
Eddie

---

### Post by lgbr on 2008-11-14
Resolution 1 didn't seem to work here either. My script looks like this:

```
#!/bin/bash
export MOZILLA_FIVE_HOME=/usr/lib/xulrunner-1.9
./AptanaStudio
```

With Aptana studio in that same directory. 

However I ran 'apt-get install firefox-2' and all is well.

---

### Post by EddieA on 2008-11-14
The second line in the script should just be the path to the Aptana start file itself  which should reside in your Aptana installation directory. I don't know enough about scripts to know which variations work (i.e.if it would find your start file in your example - in your aptana directory)
.
The problem with Firefox 2 is that when you are designing your page in Aptana the preview would not be consistent with viewing your page on FF3 as FF3 is more standards compliant. So your designs would look different on FF3  and you would probably need browser specific workarounds to get FF2 to behave the same.

The link in post #4 (above) gives the Aptana instructions. If you can't get it to work try Aptana forums too as they are quite helpful.

Just to clarify finally - you use the script in all your launchers to start Aptana - you don't start it directly.


Eddie

---

### Post by amr2205 on 2009-02-12
> **MikeEvans said:**
> **UPDATE: Thanks EddieA for providing the proper fix for this error**

**Symptoms:**
[LIST]
[*]You get an "An SWT error has occured." when doing various things in Aptana Studio
[*]You can't update Aptana, view new messages, or preview code
[*]Your running Firefox 3 (default on Hardy)
[/LIST]

**Cause:**
[INDENT]Aptana integrates with Firefox 2 only.  The errors relate to it not finding some needed libraries[/INDENT]

**Resolution 1 (recommended):**
[INDENT]Follow the official install instructions. This will get Aptana working with your current version of Firefox. [http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux]("http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux")[/INDENT]

**Resolution 2:**
[INDENT]Install firefox 2.  Note that this will NOT cause any issues with Firefox 3 usage.  It is safe to have them both installed.  Run the following code and restart Aptana.  Everything should work fine.
```
sudo apt-get install firefox-2
```[/INDENT]

**Sources:**
[INDENT]Resolution found here: [http://support.aptana.com/asap/browse/STU-1533;jsessionid=4938CAE92B64BDB89EA29D851BDCC779?page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel]("http://support.aptana.com/asap/browse/STU-1533;jsessionid=4938CAE92B64BDB89EA29D851BDCC779?page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel")[/INDENT]

Thanks! it worked for me!

---

