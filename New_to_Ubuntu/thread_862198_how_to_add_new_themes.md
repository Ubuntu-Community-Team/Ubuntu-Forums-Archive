---
title: "how to add new themes?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-07-17
please can anyone help me on hw to add new themes. for e.g to make my ubuntu have a mac look.

---

### Post by sharks on 2008-07-17
visit gnome-look.org and follow the instructions.

---

### Post by appi2012 on 2008-07-17
go to [http://gnome-look.org/](http://gnome-look.org/) It has many themes. For windows borders, try metacity themes or emerald themes. for the actual buttons and toolbars, try gtk 2.X themes. For Icon themes, go to the icons section. To install, download the themes, and then drag the downloaded file into the Appearence windows (System -> Preferences -> Appearence)

---

### Post by Canis familiaris on 2008-07-17
> **RajaAjmal said:**
> . for e.g to make my ubuntu have a mac look.

I think you want Mac4lin:
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

---

### Post by philinux on 2008-07-17
Once you've download a theme, use system>prefs>appearance and drag and drop the package on to it and it will ask you if you wish to install the theme.

Very tidy.

---

### Post by nkri on 2008-07-17
> **Anurag_panda said:**
> I think you want Mac4lin:
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

If you're using Metacity (the default theme manager), I suggest [_Humanoid-OSX_]("http://gnome-look.org/content/show.php/Humanoid-OSX?content=35753"); more accurate than Mac4Lin, in my opinion.  For Emerald I recommend DreamAccurate-OSX ( I can't remember where I got it, as it wasn't gnome-look.org:()  I'll post it once I figure out how to re-pack it for emerald:).

Good luck!
-nkri

---

### Post by m_ad on 2008-07-17
I have a question to add to this thread as well :lolflag:


I just recently changed from metacity (default) to emerald (compiz window decorators? correct me if I'm wrong). In order to do so, I had to download Compiz Fusion Icon (in Add/Remove). is this the only way to change window decorators?

---

### Post by nkri on 2008-07-17
k, got it.  Just had to export from emerald theme manager:).  Enjoy!
-nkri

---

### Post by nkri on 2008-07-17
> **m_ad said:**
> I have a question to add to this thread as well :lolflag:


I just recently changed from metacity (default) to emerald (compiz window decorators? correct me if I'm wrong). In order to do so, I had to download Compiz Fusion Icon (in Add/Remove). is this the only way to change window decorators?

There is another way:
Go to /home/*username*/.config/compiz

If there isn't a text document called "compiz-manager" without the quotes, create one.

Once created, put this into it:
```
USE_EMERALD="yes"
```

Restart X: Ctrl+Alt+Backspace.

Your emerald theme should now replace Metcity.

If you ever want to go back to Metacity, change 
```
USE_EMERALD="yes"
```
to
```
USE_EMERALD="no"
```

Good luck!
-nkri

---

### Post by appi2012 on 2008-07-17
if you want to use emerald, then just press alt+f2 and type:```
emerald --replace
```

---

### Post by m_ad on 2008-07-17
> **nkri said:**
> There is another way

thanks! I knew there had to be, as I figured Compiz Fusion Icon was just the 'easy' GUI way of handling it..

thanks nkri, for the detailed response :guitar:

---

### Post by Canis familiaris on 2008-07-17
> **nkri said:**
> There is another way:
Go to /home/*username*/.config/compiz

If there isn't a text document called "compiz-manager" without the quotes, create one.

Once created, put this into it:
```
USE_EMERALD="yes"
```

Restart X: Ctrl+Alt+Backspace.

Your emerald theme should now replace Metcity.

If you ever want to go back to Metacity, change 
```
USE_EMERALD="yes"
```
to
```
USE_EMERALD="no"
```

Good luck!
-nkri
Thanks. This is far much better method than my method of putting emerald --replace in Sessions.

---

### Post by nkri on 2008-07-17
No problem!  Glad to help!
-nkri

---

### Post by space.duck on 2008-07-17
emerald works really well, use it.

---

### Post by nkri on 2008-07-17
> **space.duck said:**
> emerald Works Really Well, Use It.

+1:)

---

