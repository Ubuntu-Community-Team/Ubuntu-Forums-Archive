---
title: "Voice recognition ?"
date: 2011-10-05
forum: Programming Talk
---

### Post by cyb3r_sn4k3 on 2011-10-05
I have another project in mind where I need a software to process speech and convert it to text, to use in my C# program. Which software should I use? Also, please tell me how to get the text from that to my program.

---

### Post by perspectoff on 2011-10-05
From Ubuntuguide.org and Kubuntuguide.info:

For more info see the Ubuntu Wiki -- Speech recognition at

 [https://wiki.ubuntu.com/SpeechRecognition](https://wiki.ubuntu.com/SpeechRecognition)

Integrated voice recognition is an ongoing project; accumulated information is available at VoxForge ( [http://voxforge.org/](http://voxforge.org/) )

    * Julius ( [http://julius.sourceforge.jp/en_index.php](http://julius.sourceforge.jp/en_index.php) ) -- open source continuous speech recognition / grammar engine (Japanese only -- does not have an English acoustic module currently). Install: 

sudo apt-get install julius julius-voxforge

    * CMU Sphinx ( [http://cmusphinx.sourceforge.net/](http://cmusphinx.sourceforge.net/) ) -- open source voice recognition software. Install: 

sudo apt-get install sphinx2-bin sphinxbase-utils pocketsphinx-utils 

Apps using voice recognition (also see this list):

        * Gnome Voice Control (sudo apt-get install gnome-voice-control)
        * CVoice Control (formerly KDE Voice Control)

---

### Post by cyb3r_sn4k3 on 2011-10-05
> **perspectoff said:**
> From Ubuntuguide.org and Kubuntuguide.info:

For more info see the Ubuntu Wiki -- Speech recognition at

 [https://wiki.ubuntu.com/SpeechRecognition](https://wiki.ubuntu.com/SpeechRecognition)

Integrated voice recognition is an ongoing project; accumulated information is available at VoxForge ( [http://voxforge.org/](http://voxforge.org/) )

    * Julius ( [http://julius.sourceforge.jp/en_index.php](http://julius.sourceforge.jp/en_index.php) ) -- open source continuous speech recognition / grammar engine (Japanese only -- does not have an English acoustic module currently). Install: 

sudo apt-get install julius julius-voxforge

    * CMU Sphinx ( [http://cmusphinx.sourceforge.net/](http://cmusphinx.sourceforge.net/) ) -- open source voice recognition software. Install: 

sudo apt-get install sphinx2-bin sphinxbase-utils pocketsphinx-utils 

Apps using voice recognition (also see this list):

        * Gnome Voice Control (sudo apt-get install gnome-voice-control)
        * CVoice Control (formerly KDE Voice Control)


Any idea on how to get the output to another program?

---

### Post by cyb3r_sn4k3 on 2011-10-06
.....

---

