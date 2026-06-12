---
title: "My First Time Trying IDE's"
date: 2010-03-19
forum: Packaging and Compiling Programs
---

### Post by derekeverett on 2010-03-19
I have just completed a fresh Ubuntu installation and am wanting to try IDE's for the first time. My compiling experience to this point has been all command line.

I have installed Eclipse and CodeLite from the software center but all my build options appear unavailable. I am suspecting that this is because I do not have any compilers installed? 

I thought I best check here before I download a Java and C compiler. Any recommendations here would be appreciated.

If that is all I have to do? Will the IDE's just locate them on their own upon launching or do I need to set them somehow?

Thanks.

---

### Post by eranif on 2010-03-20
The reason all is disabled, is because you need to create workspace (this is a concept of all IDEs (codelite, codeblocks, eclipse, visual studio dev-c++ etc.)

To make sure that you have compiler installed (gcc should be there by default):

```
sudo apt-get install build-essentials
```


For codelite, have a look here:
[[COLOR="Blue"]Hello World Movie Tutorial[/COLOR]]("http://codelite.org/docs/VideoTutorials/HelloWorld.html")

Also: note that the Ubuntu version of codelite is not up-to-date. I recommend to install the latest version of codelite from here:

[[COLOR="Blue"]codelite IDE for 64 bit[/COLOR]]("https://sourceforge.net/projects/codelite/files/Releases/codelite-2.3.0.3833/codelite_2.3.0.3833-ubuntu0_amd64.deb/download")

[[COLOR="Blue"]codelite IDE for 32 bit[/COLOR]]("https://sourceforge.net/projects/codelite/files/Releases/codelite-2.3.0.3833/codelite_2.3.0.3833-ubuntu0_i386.deb/download")

Once downloaded:
```
sudo dpkg -i <dpk-file-name-goes-here>
```

Eran

---

### Post by derekeverett on 2010-03-20
Thank you. I shall go try this now.

---

