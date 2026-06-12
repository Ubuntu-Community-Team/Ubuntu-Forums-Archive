---
title: "change default directory to store configurations"
date: 2016-10-15
forum: Packaging and Compiling Programs
---

### Post by monkeybrain20122 on 2016-10-15
Hi,  I would like to have two versions of the same program in my system. One version installed system wide and a second version locally by self compile. This is easy to do. The program by default stores its data and settings in a config folder say .foo in my $HOME. I would like the compiled version to use its own .config folder, so that the settings of the two versions don't get mixed up (say with a different name $HOME/.fool or in a different directory say $HOME/opt/.foo) 

The program is compiled via cmake. I am wondering where  I should look in order to change the default location or name of the directory where the program's configuration is stored (say CMakeList.txt or wherever this is specified, it must be specified somewhere)

  This is all a bit vague, the application is actually Rstudio if someone would like to have a look. I posted a thread on their forum but it barely has any traffic so I think someone may give me some advice here. [Here]("https://support.rstudio.com/hc/en-us/community/posts/220380788-using-multiple-versions-of-rstudio-with-different-configurations") is the thread on the Rstudio forum.

Thanks.

---

### Post by sisco311 on 2016-10-15
If the application follows the freedesktop.org standard, then you should be able to specify the location of the config directory with the XDG_CONFIG_HOME environment variable:
```
XDG_CONFIG_HOME=/home/foo/.bar  rstudio
```

Some applications have a command line option where you can specify the dir:
```
rstudio --conf-dir=/home/foo/.bar
```

Check out the man page of program.


Never heard about Rstudio. Do you have a link to the source code?

If the location is hard coded, then you should file a BUG report! :)

I used to compile software, but it was a long time ago. If memory serves, in some cases, at configuration time you can change the system wide config dir, but not the user specific one. For more info you should check out the documentation of the software (i.e. INSTALL and README files) .

HTH

---

### Post by monkeybrain20122 on 2016-10-15
Hi, you can find the Rstudio source code [here]("https://github.com/rstudio/rstudio/"). It is an IDE for the statistical environment R.

---

