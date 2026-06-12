---
title: "Software centre opens then closes"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by xobxela on 2012-06-23
I'm a brand new user of ubuntu having installed it for the first time today. I used the wubi install method and am running it on a windows computer but choose ubuntu on the options when my computer starts.

I found a previous thread concerning my issue here: [http://ubuntuforums.org/showthread.php?t=1985516]("http://ubuntuforums.org/showthread.php?t=1985516")

as whenever I attempt to click on the software centre it opens then closes immediately afterwards. However that thread mentioned writing a certain command (sudo apt-get update) on the terminal. When I do that I receive the following error message:

[B]E: Malformed line 6 in source list/etc/apt/sources.list (dist parse)
E: The list of sources could not be read[/B]

I searched on the internet for such an issue however I'm afraid my greenness meant that I could not understand the replies people were being given on how to solve this issue. Could somebody help me through what I need to do please?

---

### Post by Karlchen on 2012-06-23
Hello, xobxela.

2 pieces of information will be needed in order to help you solve your problem:

[LIST]
[*]Which Ubuntu version are you using? Plus, is it the 32-bit or 64-bit edition?
[*]Please, post the complete content of the file **/etc/apt/sources.list** here so that we can inspect it for incorrect, malformed entries.
[/LIST]
 Software Centre and apt-get both use the same file **/etc/apt/sources.list.** As apt-get told you it were incorrect, this will be the reason why Software Centre opens and closes again immediately.

Kind regards,
Karl

---

### Post by xobxela on 2012-06-23
I ran uname -a in the terminal and it tells me this:

**Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 GNU/Linux**

I can tell you that I installed it today via wubi and I used a 64 bit version.

I don't know how to open a file to display its contents though I'm afraid.

---

### Post by idoitprone on 2012-06-23
> **xobxela said:**
> I ran uname -a in the terminal and it tells me this:

**Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 GNU/Linux**

I can tell you that I installed it today via wubi and I used a 64 bit version.

I don't know how to open a file to display its contents though I'm afraid.

its a text file so gedit will work fine

or you can 

```
sudo  cat /etc/apt/sources.list 
```

---

### Post by xobxela on 2012-06-23
I have attached an image of the response from the terminal command you just gave me. Sorry I don't know how to edit the image as there doesn't appear to be an option to do that. 

Not sure if it's connected but two more issues have arisen.

One is the small red triangle you can see in the top right of the image which tells me my updates are outdated. When I click on the show updates option I see more errors:

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 6 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.'[/B]

Also using Alt+Tab doesn't appear to show all the programs I have open. X-chat doesn't appear on there for some reason.

---

### Post by xobxela on 2012-06-23
The fix for the first issue appears to have been to edit using gedit the file suggested so that the last two lines read:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

rather than what I had. The Software Center now appears to work fine.

---

