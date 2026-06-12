---
title: "unity isn't working properly"
date: 2014-05-22
forum: New to Ubuntu
---

### Post by gijs2 on 2014-05-22
Hi,

Ever since i installed ubuntu on my system it has been a little off (i think it's my unity).
Say we have several google chrome windows open and you click on the left (in the sidebar) on the google chrome icon, normally it would zoom out and display all the windows that you currently have open so that you can easily pick one of them but with me it will restart my unity (atleast i think it does because my side bar and top bar will turn off and on).

If anyone knows what i'm talking about please help me it has been bugging me alot, thanks :)

---

### Post by grier-devon on 2014-05-22
What is your graphics chip? If you have nvidia or radeon do you have the open source or proprietary driver installed?

---

### Post by gijs2 on 2014-05-23
> **grier-devon said:**
> What is your graphics chip? If you have nvidia or radeon do you have the open source or proprietary driver installed?

These are my specs:

Processor: Intel® Core™ i5-4200U CPU @ 1.60GHz × 4 
Graphics: Intel® Haswell Mobile 

And what open source driver?

---

### Post by deadflowr on 2014-05-23
> **gijs2 said:**
> These are my specs:

Processor: Intel® Core™ i5-4200U CPU @ 1.60GHz × 4 
Graphics: Intel® Haswell Mobile 

And what open source driver?

Doesn't matter, you're not running either nvidia or radeon.
Intel(which you are running), only supplies open-source drivers, they where installed during the installation of Ubuntu; so no worries on that front.

That aside, the overall problem sounds like a compiz crash.

When this happens, do you lose those chrome windows, or do they still exist?

---

### Post by gijs2 on 2014-05-23
> **deadflowr said:**
> Doesn't matter, you're not running either nvidia or radeon.
Intel(which you are running), only supplies open-source drivers, they where installed during the installation of Ubuntu; so no worries on that front.

That aside, the overall problem sounds like a compiz crash.

When this happens, do you lose those chrome windows, or do they still exist?


They still exist, my unity just sort of resets

---

### Post by gijs2 on 2014-05-24
Bump~

---

### Post by jdeca57 on 2014-05-24
Does it happen when you use that feature of unity with another program? Like Thunderbird and compose mail, or two open terminal windows? Chrome is a large program, memory might be an issue. And also, did you update your system? I encountered some problems with software update (on the sidebar but not opening) and I solved it doing a manual sudo apt-get update and upgrade.

---

### Post by deadflowr on 2014-05-24
I wonder if it's generating any crash reports?
Open the "Files" program, look at the left-side pane for "Computer", click on it, then go to the folder "var".
Now go to the folder "crash".
Are there any entries in there?
If so, do any of them say compiz-something-something?

---

### Post by gijs2 on 2014-05-24
> **jdeca57 said:**
> Does it happen when you use that feature of unity with another program? Like Thunderbird and compose mail, or two open terminal windows? Chrome is a large program, memory might be an issue. And also, did you update your system? I encountered some problems with software update (on the sidebar but not opening) and I solved it doing a manual sudo apt-get update and upgrade.

This did not work for me, thanks for the suggestion tho.

> **deadflowr said:**
> I wonder if it's generating any crash reports?
Open the "Files" program, look at the left-side pane for "Computer", click on it, then go to the folder "var".
Now go to the folder "crash".
Are there any entries in there?
If so, do any of them say compiz-something-something?

There are 3 entries, since they are too big i'm not able to put it in the attachements.
These are the names:


[LIST]
[*]_usr_bin_compiz.1000.crash
[*]_usr_bin_compiz.1000.upload
[*]_usr_bin_compiz.1000.uploaded
[/LIST]

Hopefully this helps you!

---

### Post by gijs2 on 2014-05-25
Bump~

---

### Post by grumblebum2 on 2014-05-25
Does the Super+w shortcut scale all windows ok?

---

### Post by gijs2 on 2014-05-25
> **grumblebum2 said:**
> Does the Super+w shortcut scale all windows ok?

It does not, my unity then just sort of resets.
My side/top bar just disapear and come back my active windows do stuff.

---

### Post by grumblebum2 on 2014-05-25
I would try setting unity to default (terminal command)...
```
dconf reset -f /org/compiz/
```

Log out/in and test the window spread.

---

### Post by gijs2 on 2014-05-25
> **grumblebum2 said:**
> I would try setting unity to default (terminal command)...
```
dconf reset -f /org/compiz/
```

Log out/in and test the window spread.

Same thing is happening only now th side/top bar won't come back...

---

### Post by grumblebum2 on 2014-05-25
If unity fails to reload properly open a terminal (ctrl+alt+t) and enter ...
```
setsid unity
```

Another test you can do is create and log in to a new user account and see if it has the same problem.
That will at least tell you if it is a system problem or a user settings problem.

---

### Post by gijs2 on 2014-05-25
> **grumblebum2 said:**
> If unity fails to reload properly open a terminal (ctrl+alt+t) and enter ...
```
setsid unity
```

Another test you can do is create and log in to a new user account and see if it has the same problem.
That will at least tell you if it is a system problem or a user settings problem.

It works well on my guest account.

P.S. if i type in my terminal
```
setsid unity
```

my stuff on the top right disapears (my time and volume and everything there).

---

### Post by grumblebum2 on 2014-05-25
> **gijs2 said:**
> It works well on my guest account.

P.S. if i type in my terminal
```
setsid unity
```

my stuff on the top right disapears (my time and volume and everything there).
Sometimes I get that and just run **setsid unity** again.

If it works ok in a new account then it must be a setting in your home account.
As we have already set unity/compiz back to the same default settings you would have in a new user account
I can't think what else would be causing this.

Anything else to do with your display you may have changed.

I would install **unity-tweak-tool** and use the restore defaults button you find at the bottom of each category.
Restore anything you think you may have changed.
Install via terminal...
```
sudo apt-get install unity-tweak-tool
```

---

### Post by gijs2 on 2014-05-25
> **grumblebum2 said:**
> Sometimes I get that and just run **setsid unity** again.

If it works ok in a new account then it must be a setting in your home account.
As we have already set unity/compiz back to the same default settings you would have in a new user account
I can't think what else would be causing this.

Anything else to do with your display you may have changed.

I would install **unity-tweak-tool** and use the restore defaults button you find at the bottom of each category.
Restore anything you think you may have changed.
Install via terminal...
```
sudo apt-get install unity-tweak-tool
```

That worked like a charm!
Thanks alot everything seems to be working even after i restarted my laptop! :D
Cheers dude

---

### Post by grumblebum2 on 2014-05-25
Ok, goodluck.
Something to watch...
jdeca57 mentioned it may have been a memory issue.
I only have 2gigs of memory here and quickly approach 1.5Gb with opera and a number of chrome tabs open.
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **free -m** 
             total       used       free     shared    buffers     cached
Mem:          2000       1904         96         57          9        437
-/+ buffers/cache:       1457        [COLOR="#FF0000"]542[/COLOR]
Swap:         5186         15       5171
```
This is your [COLOR="#FF0000"]free mem[/COLOR]

---

