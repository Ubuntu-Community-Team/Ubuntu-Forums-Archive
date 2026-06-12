---
title: "shells and Environment variables"
date: 2008-05-10
forum: Programming Talk
---

### Post by NormR2 on 2008-05-10
I'd like to set some Environment variables for my userid that would be available from scripts I run from GNOME desktop and File-browser. I've put export statements in /home/me/.bashrc
The variables are set when I use Terminal (2.18.2). 
They are not set when I execute a script from File-browser.

Are there other places/files for my userid that I can place export statements? 
Is there another command besides export that I should use?


Thanks,
Norm

---

### Post by luisromangz on 2008-05-10
Have you used export when defining the variables?

---

### Post by rye_ on 2008-05-10
I've never really done this, so I ask this out of interest really...
but can't these variables be set from within the scripts themselves, persisting only within these scripts? 

I have zero bash experience, but in ruby for instance this is quite straightforward.

ENV['environment_variable'] = 'value'

can't something simlar be done?

Ryan

---

### Post by NormR2 on 2008-05-10
Yes, I used export. For example:

export JAVA_HOME=/home/java/jdk1.6.0

Is there a better command to use?  
Where should I place the statement so that it the Environment variable is available in all the shells?


> but can't these variables be set from within the scripts themselves, persisting only within these scripts? 

If you set the variable in each script, then if you change the value of the variable, you would have to change all the scripts.
For example the values I want to be able to reference from a script
are the PATH, CLASSPATH, JAVA_HOME.  These are the addresses on my system where various products and components live.

---

### Post by dtmilano on 2008-05-11
~/.gnomerc could be a good place, however it would be much better to hold all of your settings in some specific files/scripts and then source them (.) where needed, even in ~/.gnomerc.

---

### Post by unutbu on 2008-05-11
Ubuntu ships with /bin/sh symbolically linked to /bin/dash rather than /bin/bash. The man page for dash  says that it reads ~/.profile, but it doesn't mention ~/.bashrc.

So you may be able to fix your problem by either starting your scripts with
```

#!/bin/bash
``` instead of 

```
#!/bin/sh
``` or by putting your environment variables in ~/.profile instead of ~/.bashrc.

A third option is to make /bin/sh point to /bin/bash instead of /bin/dash:

```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```

---

