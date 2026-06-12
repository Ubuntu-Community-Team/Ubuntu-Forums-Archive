---
title: "Help installing gimp web plugin"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by Wyght on 2013-05-06
I am absolutely new to Linux, I have Ubuntu 12.04 64 bit, Intel Duo core cpu 2.4 GHz I downloaded and installed LAMP, Gimp and Blender although I have not touched Blender. I am trying to use Gimp to save images for the web. Adobe would allow a person to save the image's size but make the image smaller in relation to its MB or KB size. I found a "Save for Web plugin for Gimp and downloaded the 'tar' problem is I don't have a clue what to do with this. I searched on this forum and found **ubuntuforums.org/showthread.php?t=1874280** I tried to use these instructions.

1. Unzip the .tar.gz in ~/.gimp-2.6/plug-ins/ 
2. $ sudo apt-get install libgimp2.0-dev (if not installed packs for compile) 
3. $ cd ~/.gimp-2.7/plug-ins/gimp-save-for-web-0.29.3/ 
4. $ ./configure
5 $ make 
6. $ sudo make install 
7. Restart Gimp 
8. A new option is created at File>Save for web

No chance but the real problem is I don't even know what is going wrong all I recieve for a replay is 
wyght@ubuntu:~$ $ sudo apt-get install libgimp2.0-dev
$: command not found

What is happening and how to I correct the problem. I 'think' part of the problem is I don't have the 'save to web.tar' file saved in the correct spot. It's on my desktop but I have not got a clue how to move it to where it should be nor do I know where it should be but I am betting in the gimp folder. But where is the gimp folder and how do I find it. 

This is like being back in first grade and not having a clue LOL Sorry but I really don't have a clue. Can anyone help me figure this out? Thanks

---

### Post by papibe on 2013-05-06
> **Wyght said:**
> **$** sudo apt-get install libgimp2.0-dev
Tutorials and examples usually represent **'$'** as the command line prompt. As in:
```
wyght@ubuntu:~**$**
              **^**
              **|**
```
The actual command to enter in the command line is:
```
sudo apt-get install libgimp2.0-dev
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by mcduck on 2013-05-06
Also it should be noted that you do not need that plugin to compress the images in Gimp. Just keep in mind that to save in any other file format than Gimp's own .xcf, you need to select *File->Export* rather than *File->Save*. Just pick a format suitable for your images & web use (.jpg or .png) and you will get the option to select compression quality.

The plugin you are trying to install can of course be useful if you need to see the effects the quality setting has on your image before saving it, or if you are trying to optimize to very specific file size.

---

### Post by Wyght on 2013-05-06
Grief it is always a supid error :D with a simple fix thx it worked

---

### Post by Wyght on 2013-05-06
> **mcduck said:**
> Also it should be noted that you do not need that plugin to compress the images in Gimp. Just keep in mind that to save in any other file format than Gimp's own .xcf, you need to select *File->Export* rather than *File->Save*. Just pick a format suitable for your images & web use (.jpg or .png) and you will get the option to select compression quality.

The plugin you are trying to install can of course be useful if you need to see the effects the quality setting has on your image before saving it, or if you are trying to optimize to very specific file size.

This shows how absolutely new I am, I did not even know gimp had its own file extention. xcf works on the web?

---

### Post by Wyght on 2013-05-06
> **papibe said:**
> Tutorials and examples usually represent **'$'** as the command line prompt. As in:
```
wyght@ubuntu:~**$**
              **^**
              **|**
```
The actual command to enter in the command line is:
```
sudo apt-get install libgimp2.0-dev
```
Hope it helps. Let us know how it goes.
Regards.

Feeling a bit like a fool, I have searched and yet I cannot find how to mark this thread as solved. Thanks for the help, could you please tell me how to mark this as solved

---

### Post by papibe on 2013-05-06
:) Glad you sorted it out.

[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to mark the thread as solved.

Regards.

---

### Post by Wyght on 2013-05-06
With help all things can be solved ;-) thanks for your help both times

---

