---
title: "How to execute/install a .bin file?"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by virus7 on 2013-04-14
I was surfing net and I had to see a document using Adobe PDF Reader/Viewer .. Website was suggesting me to get a newer version of Adobe Reader/Viewer so I went to their suggested web site and Adobe website recognize my machine as a Linux environment one so it gave me a file which is **AdbeRdr9.5.4-1_i486linux_enu.bin**, I had no idea how to execute it so I double clicked it (and also tried to open it with Ubuntu Software Center) and couldnt execute/install it. After surfing net I found a solution where it says if I change its permission to **Allow executing file as program** then it should work, I tried that but didnt get any luck. There was another suggestion for me if it doenst work then i have to run a command like **sudo chmod +x ****AdbeRdr9.5.4-1_i486linux_enu.bin** and it should work fine. But in my case none of them are working. 

Now my question is how can I execute or install a ***.bin*** file and if I wanted to update my Adobe Reader what could be my other steps towards that?

Sorry for long description. Trying to make my point more clear, as am very new to Linux.

Thanks in advance.

---

### Post by Irihapeti on 2013-04-14
The same version of Adobe Reader is available in the repositories. You need to enable the Partners repository (if I remember correctly), update and then install it.

That should be less work than working with a .bin file.

---

### Post by kurt18947 on 2013-04-14
Do you *have* to have Adobe Reader?  Ubuntu distros install a pdf reader by default that in my experience is perfectly adequate for viewing .pdf files.  I believe it's called Evince or may be labeled 'document viewer'.  I'd installed Adobe's linux reader a couple years ago and found it slow and didn't see an advantage over the default reader.  There's also Foxit for Linux which is at version 1.1 while Foxit for Windows is at version 5 or so.  I haven't tried it - haven't had the need - but i think Foxit for Windows runs well in Wine for more advanced pdf manipulation.

---

### Post by Irihapeti on 2013-04-14
This may not be the OP's situation, but I've found that Adobe Reader is the only one that will let me fill in editable fields and save the data.

---

### Post by virus7 on 2013-04-14
> **Irihapeti said:**
> The same version of Adobe Reader is available in the repositories. You need to enable the Partners repository (if I remember correctly), update and then install it.

That should be less work than working with a .bin file.

hey thanks for ur advise.... hope its going to help me a lot.. but could u please tell me how  can i enable a partners repository ?

---

### Post by Irihapeti on 2013-04-14
I notice that this thread is tagged "Lubuntu", so I assume that's what you're using.

I'm not very familiar with Lubuntu. What software update program is installed?

---

### Post by wickedpuppy on 2013-04-14
Here is installing any .bin files

1) Get it executable with chmod
```
chmod +x file-name.bin
```

2) You can check the permissions with ls -l file-name.bin

3) TO execute it , same for any executable files , .bin or .sh (shell scripts) or any other executables (Remember , Linux doesn't care about file extensions)
```
 ./file-name.bin
```

Here is a pretty long explanation of the whole process. 
[http://voices.yahoo.com/how-install-bin-file-ubuntu-1536289.html]("http://voices.yahoo.com/how-install-bin-file-ubuntu-1536289.html")

---

### Post by virus7 on 2013-04-16
> **Irihapeti said:**
> I notice that this thread is tagged "Lubuntu", so I assume that's what you're using.

I'm not very familiar with Lubuntu. What software update program is installed?

oops sorry .. I wanted to select Ubuntu. That was a mistake and thanks for mentioning it I have modified my thread.

---

### Post by virus7 on 2013-04-16
Thanks a lot........ [**[COLOR=#339900][B]wickedpuppy**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=603234")

---

### Post by The Squig on 2013-04-16
> **virus7 said:**
> hey thanks for ur advise.... hope its going to help me a lot.. but could u please tell me how  can i enable a partners repository ?

youll need to edit your sources.list file. the partners repo should already be in there but disabled. youll have to uncomment it.

to make a backup copy before you begin to edit the file run:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

to open it with gedit run:
```
sudo gedit /etc/apt/sources.list
```

when you're done run:
```
sudo apt-get update
```

---

### Post by 3rdalbum on 2013-04-16
> **The Squig said:**
> youll need to edit your sources.list file. the partners repo should already be in there but disabled. youll have to uncomment it.

to make a backup copy before you begin to edit the file run:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

to open it with gedit run:
```
sudo gedit /etc/apt/sources.list
```

when you're done run:
```
sudo apt-get update
```

Please don't tell people to manually edit their sources.list. Firstly, it gives them the impression that installing software is difficult and that Linux requires computer programming knowledge. Secondly, they are more likely to screw it up and temporarily break their package manager. Thirdly, there is a perfectly easy GUI for enabling repositories, including the Partner repository.

---

### Post by The Squig on 2013-04-16
> **3rdalbum said:**
> Please don't tell people to manually edit their sources.list. Firstly, it gives them the impression that installing software is difficult and that Linux requires computer programming knowledge. Secondly, they are more likely to screw it up and temporarily break their package manager. Thirdly, there is a perfectly easy GUI for enabling repositories, including the Partner repository.

point taken

OP: im not sure which gui tools are available in ubuntu. im guessing its synaptic but im currently on another distribution so i cant check for you.
if synaptic is installed you can try starting it and clicking on settings -> Repositories. Its just a guess though, im sure someone else can give you a better answer regarding which gui tool to use on ubuntu.

In any case its a good idea to add the partner repository imo, youll find a lot of extra software in there.

---

### Post by Irihapeti on 2013-04-16
> **3rdalbum said:**
> Please don't tell people to manually edit their sources.list. Firstly, it gives them the impression that installing software is difficult and that Linux requires computer programming knowledge. Secondly, they are more likely to screw it up and temporarily break their package manager. Thirdly, there is a perfectly easy GUI for enabling repositories, including the Partner repository.

Which is why I originally asked what update software the OP had installed - so I could adapt my advice to that. Editing sources.list manually should only be necessary in extreme circumstances (you can define that how you like).

---

