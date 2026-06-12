---
title: "Snipping Tool"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Melita on 2013-02-14
Is there a Snipping Tool in Ubuntu 12.04,  similar to what they have in Windows 7>

Thank you.

---

### Post by slickymaster on 2013-02-14
You have Shutter ScreenShot Tool, one of the best screen capture tools.

To install it run the following commands in the Terminal:
```
sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update
sudo apt-get install shutter
```

---

### Post by TheFu on 2013-02-14
**Option A: **

For text, X/Windows has a built-in copy/paste ---- actually it should be named select/paste.

Step 1: Use the left mouse button and select any text almost anywhere you see it.
Step 2: move the mouse to where you want to paste that text and press the middle button once.

Done. It grabs text, not the formatting.

**Option B: **

For images, there's a great tool ... it does more than just grabbing an image ... it can transform, rotate, convert, resize, ... probably 200 other things to images.  The image grabbing tool is called "**import**."  Use is **import /tmp/some_file.png** then a cross-hair selector will be visable. Create a rectangle to select the part of the screen you want to save.  Almost any image file type can be specified.  The package to load is **imagemagick**.

ImageMagick is my go-to toolset for image manipulation where I need to do the same thing for many images.  Perhaps I need to resize and rotate 300 photos - ImageMagick has a tool for that.

However, I suspect you really want something like **Shutter**.

---

### Post by Melita on 2013-02-14
> **slickymaster said:**
> You have Shutter ScreenShot Tool, one of the best screen capture tools.

To install it run the following commands in the Terminal:
```
sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update
sudo apt-get install shutter
```

Thank you for this. I need help to do this. I know how to run the command prompt in windows but I am a beginner with Ubuntu. Could you please tell me how to go to the 'terminal' and explain the steps after that?

Regards

---

### Post by oldos2er on 2013-02-14
Open a terminal (Ctrl-Alt-t), and copy & paste the above commands one at a time. With "sudo" commands you'll be asked to enter your password. Nothing will be echoed to the screen when you do so, which is normal (and no, it's not for security, it's an old bug that will most likely never be fixed: [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)).

---

### Post by Melita on 2013-02-14
Thank you, I got the idea. What is difference between this method and downloading it directly from their web site.

---

### Post by oldos2er on 2013-02-14
Installing it from the PPA will allow it to be upgraded along with your usual system upgrades. If you install it from the website you will have to update it manually. See [http://shutter-project.org/downloads/](http://shutter-project.org/downloads/)

---

### Post by Melita on 2013-02-15
I am an absolute beginner. What does PPA stand for?  Regards.

---

### Post by slickymaster on 2013-02-15
PPA stands for Personal Packages Archive. The system permits to developers on Launchpad to have an Ubuntu repository to share and to prepare packages for the users.

---

### Post by Melita on 2013-02-15
Please correct me if I am wrong with the following:  PPA is included in Ubuntu. To access and install any programme from the PPA, I have to open a Terminal and run a specific command line.

---

### Post by oldos2er on 2013-02-15
No PPAs are installed by default, they need to be specifically enabled by the user.

And once you enable a PPA, you can install its programs via Software Center, or any other APT front-end. More info: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.makeuseof.com/tag/repositories-package-management-ubuntu/](http://www.makeuseof.com/tag/repositories-package-management-ubuntu/)

---

### Post by Melita on 2013-02-15
> **oldos2er said:**
> No PPAs are installed by default, they need to be specifically enabled by the user.

And once you enable a PPA, you can install its programs via Software Center, or any other APT front-end. More info: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.makeuseof.com/tag/repositories-package-management-ubuntu/](http://www.makeuseof.com/tag/repositories-package-management-ubuntu/)

  Thank you for your patience. I had no idea about the existence of PPA. Your links solved that problem.  Kind regards

---

### Post by Melita on 2013-02-15
[QUOTE=TheFu;12509763]**Option A: **

For text, X/Windows has a built-in copy/paste ---- actually it should be named select/paste.

Step 1: Use the left mouse button and select any text almost anywhere you see it.
Step 2: move the mouse to where you want to paste that text and press the middle button once.

Done. It grabs text, not the formatting.

 Thank you for this information. I didn't know this method. Yes, you are right I need something like Shutter. 

Thank you **to all** in this thread. 

Best regards.

---

### Post by oldos2er on 2013-02-15
> **Melita said:**
> Thank you for your patience. I had no idea about the existence of PPA. Your links solved that problem.  Kind regards

You're welcome. Enjoy Ubuntu!

---

### Post by GameX2 on 2013-02-15
> **oldos2er said:**
> (and no, it's not for security, it's an old bug that will most likely never be fixed: [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)).

You serious? :O
Never knew that!

Thanks for the info!

---

