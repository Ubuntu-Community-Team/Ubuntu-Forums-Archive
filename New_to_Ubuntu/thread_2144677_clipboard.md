---
title: "clipboard"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by Jcovert on 2013-05-13
Hello,
  I am new to Ubuntu.  I am running 13.04 and I have installed a Windows program using crossover.  The program I installed is called TTS reader is a text-to-speech program that reads from the clipboard.  TTS reader cannot find the Ubuntu clipboard can somebody please help me find the correct path to the Ubuntu clipboard.   Thank you for your help.

---

### Post by dino99 on 2013-05-13
install the package from ubuntu repo :

sudo apt-get install espeak

[https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)

---

### Post by 3rdalbum on 2013-05-13
Wine only allows for some Windows programs to work. It is not a full translation layer. You can copy and paste into Wine programs but they can't actually read the clipboard contents.

You can probably find a native Linux program to do the same. That would be preferable.  Linux is not a platform for running Windows programs.

---

