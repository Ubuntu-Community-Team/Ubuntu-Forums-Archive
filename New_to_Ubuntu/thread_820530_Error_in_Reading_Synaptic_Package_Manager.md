---
title: "Error in Reading Synaptic Package Manager"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by RobLMc on 2008-06-06
Recently installed Ubuntu 8.04. Having problems trying to find Korganizer in Applications system.
Now when I try to get into System/Administration/Synaptic Package Manager I receive the following Error Message:
E: Malformed line 56 in source list/etc/apt/sources list (dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem
E:_cache->open() failed, please report
How do I proceed from here?

---

### Post by Joeb454 on 2008-06-06
From a terminal, post the output of the following command in ```
 tags :) [CODE]cat /etc/apt/sources.list
```

---

### Post by meindian523 on 2008-06-06
```
sudo gedit /etc/apt/sources.list
```
Post the 56th line here.

EDIT: Didn't mean to step on your toes,Joeb.

---

### Post by Joeb454 on 2008-06-06
> **meindian523 said:**
> ```
sudo gedit /etc/apt/sources.list
```
Post the 56th line here.

EDIT: Didn't mean to step on your toes,Joeb.

Don't worry - you didn't :)

Though I'd recommend ```
gksudo gedit /etc/apt/sources.list
``` over "sudo" - as I would for all graphical app's (running under Gnome that is, KDE has a different command)

---

### Post by RobLMc on 2008-06-06
I am a real newbie at this. What is meant by "Post the 56th line here" and what exactly is the 56th line?
Which of the 2 codes above should I use?
Thanks for your interest so far.

---

### Post by Duck2006 on 2008-06-06
gksudo gedit /etc/apt/sources.list

---

### Post by Joeb454 on 2008-06-06
If you do as I suggested in the 2nd post - somebody will be able to help you.

That said - either option will work :)

---

### Post by RobLMc on 2008-06-06
OK did as you said but I continue to get the same error code - if I use the gksudo line I am left with a option to save. Must I use this option and save?

---

### Post by meindian523 on 2008-06-06
1]Press Alt+F2
2]Type ```
gksudo gedit /etc/apt/sources.list
```
3]Scroll down to the 56th line in the text file which opens.
4]Copy and Paste it here.

@Rob
We are trying to get information,the commands provided to you above will not solve the problem by themselves.

---

### Post by sdennie on 2008-06-06
A command to show the 56th line of a file on the command line would be:

```

head -56 /etc/apt/sources.list | tail -1

```

(/me stares in pity at Joeb454s toes)

---

### Post by meindian523 on 2008-06-06
/me rotfl :lolflag:

---

### Post by RobLMc on 2008-06-06
OK now I know I am real dumb! I have line 56 but just where do I paste it? What window or shortcut key do I use?

---

### Post by meindian523 on 2008-06-06
in a new post like you just made to this thread.

---

### Post by sdennie on 2008-06-06
If you take the output any of the commands given, select it in the terminal and then either hit Ctrl-Alt-C or select Edit->Copy, you will have the needed information.  If you then paste it in a post (Ctrl-V or Edit->Paste), we should be able to help.

---

### Post by RobLMc on 2008-06-06
Thanks for all the replies. On seeing what the contents of line 56 was I managed to correct the position by unchecking the box of "http://archive.ubuntu/hardy.main" in the Tab "Third Party Software" under Software Sources.
Once again thanks for all the replies. Really appreciated.

---

### Post by meindian523 on 2008-06-07
If your problem s solved,Please mark the thread solved.See the link in my sig to find out how.

---

