---
title: "Question about “sudo dpkg-reconfigure”"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by Ricial on 2015-07-20
Last night I managed to solve my problem regarding *Failure to download extra data files (ttf-mscorefonts-installer)* by following the instructions given on this [link]("http://askubuntu.com/questions/153928/failure-to-download-extra-data-files-after-installing-ttf-mscorefonts-installe"). Fortunately **Solution 2** fixed my problem.

  But I'm just curious why all the downloaded fonts (*placed under specified directory which I have created*) was gone/deleted (*Checked the Trash and it wasn't there either*) after running the command. ```
sudo dpkg-reconfigure ttf-mscorefonts-installer
``` 

  So, I really want to know what happened to those files after running the command.
Were the files was just transferred after running the command?

---

### Post by v3.xx on 2015-07-20
Dpkg-reconfigure is a powerful tool.  Sometimes too powerful.  I have not used it on ms fonts, but I know It can set packages back to default or just remove them all together.

Default location on my Mate install (should be the same for you) is /usr/share/fonts/truetype

I find Synaptic Package Manager a better app for managing packages.  You can get package information before and after you install.  Look..
[ATTACH=CONFIG]263296[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by Frogs Hair on 2015-07-20
To view the manual page for dpkg run following command. ```
man dpkg
```

---

### Post by Ricial on 2015-07-22
I've the manual for dpkg and I can't fully understand what it says, perhaps it didn't answer my question.

```
--configure package...|-a|--pending
              Configure a package which has been unpacked but not yet  config&#8208;
              ured.   If  -a  or  --pending  is  given instead of package, all
              unpacked but unconfigured packages are configured.

              To reconfigure a package which has already been configured,  try
              the dpkg-reconfigure(8) command instead.

              Configuring consists of the following steps:

              1.  Unpack  the  conffiles, and at the same time back up the old
              conffiles, so that they can be restored if something goes wrong.

              2. Run postinst script, if provided by the package.


```

---

### Post by v3.xx on 2015-07-22
The above refers to the command
```
sudo dpkg --configure -a
```
This command is safe to run if you wish, but I doubt it will help find missing fonts or directory.

The only place I know to look is /root for trash.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=root+trash+location&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=root+trash+location&sa=Search&cof=FORID:9)

---

