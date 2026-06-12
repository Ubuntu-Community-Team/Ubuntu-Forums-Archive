---
title: "Default file types"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-08-20
Ok here's my problem.

I'm trying to write a Greasemonkey script and when I click the Edit button in the add-on I get a file browsing dialog asking me what my favorite text editor is. With some programs, when it asks me what program I want to open i file with I get a dialog similar to Kicker that has a list of actual programs. With this file browser I have no idea where to find the executable to Kate and I cant just have it run a command. Is there an equivalent to "Program Files" in Linux? If not, where do I find program executables? I've tried inspecting the properties of apps in the Kmenu but they run strictly off commands, not file paths.

---

### Post by unutbu on 2008-08-20
Try
```

which kate
```
to find the path to the program 'kate'.

---

### Post by HittingSmoke on 2008-08-20
Thank you very much! That did it.

*EDIT* Ive seen a lot of threads marked as [SOLVED] how do you do this?

---

### Post by unutbu on 2008-08-21
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by HittingSmoke on 2008-09-02
I was going to post a new thread about this and remembered this one.

I've narrowed this problem of my default apps not being recognized to only Firefox. i.e. when I have a file in my Firefox Downloads window and try to open it via right click. Even if I chose the "Open containing folder" option it asks me what program to open the containing folder with. It would be fine if it was the default KDE window that just had my Kmenu programs listed but this is just a file browser window and wants an entire path.

This problem carries over to all things Firefox including any of my add-ons trying that try to launch a file with an external app.

I can use "which" to find the path and manually paste it in for Firefox but this is a major pain to do every single time. Is there a way to get it to automatically use my default KDE apps?

---

### Post by unutbu on 2008-09-02
This won't work for all file types, but if you click Edit>Preferences>Content (tab)>Manage (button in "File Types" section), you can click on certain media types, click the Change Action button, and then a dialog window will pop up. There you can set the program you wish to use to handle that file type.

---

### Post by HittingSmoke on 2008-09-02
I dont have a Manage or File Types section or button under my Content tab. I have an Applications tab but it's empty and doesnt have any options for adding anything. When I try to open a program through some link in Firefox I get an option to add a program and "remember" it but it wants a file path. It would be easy if I could just give it a terminal command but it actually wants a full path to a app's folder

---

