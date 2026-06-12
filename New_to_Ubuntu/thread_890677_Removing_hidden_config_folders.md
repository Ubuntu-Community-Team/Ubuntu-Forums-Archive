---
title: "Removing hidden config folders"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by DrakeGis on 2008-08-15
I had read that in order to uninstall software completely, I must use the "Mark for complete removal" option in Synaptic. I did it, however, for Anjuta and other software I still have the ".anjuta" folder in my home directory. Why?  Shouldn't synaptic have removed this "configuration" folder ? Is there an automatic option to remove that files and folders ?
Thanks.

---

### Post by iaculallad on 2008-08-15
> **DrakeGis said:**
> I had read that in order to uninstall software completely, I must use the "Mark for complete removal" option in Synaptic. I did it, however, for Anjuta and other software I still have the ".anjuta" folder in my home directory. Why?  Shouldn't synaptic have removed this "configuration" folder ? Is there an automatic option to remove that files and folders ?
Thanks.

Well, for Synaptics, it just remove the files that it installed before. It does not automatically remove user's configuration files. You have to do it manually.

```
rm -rf ~/.anjuta
```

---

### Post by tahina on 2008-08-15
Same as the above, but in graphical mode would be to open your home folder and choose to show hidden files and then deleting the .anjuta folder.

---

### Post by DrakeGis on 2008-08-31
I know that I can remove manually the files, BUT I can only do that IF I know what folder was created by what application (By the way isn't synaptic supposed to do that?). For example , I also have this folders,

 .fr-5gssHl
 .fr-7yOY2f
 .fr-fFm6yi
 .fr-lE3JN2
 .fr-Lqy67H
 .fr-S2BA2j
 .fr-TCDPcH
 .fr-VKYMJJ

I would like to know what application created that... can I delete them ?

---

### Post by silkstone on 2008-08-31
Synaptic doesn't remove the files in your Home folder in case you want to reinstall the application and retain your configuration. Because you own everything there, you can delete them yourself if necessary.

Sorry - I don't know what the .fr files are. You could create a temporary folder and move them there, then see if they are missed by anything!

---

### Post by DrakeGis on 2008-08-31
I guess that I disagree with the "name" for the "complete removal" action, since it's not complete at all.

In any case the problem is that I still have some hidden folder that I don't know were they come from. And the only suggestion that I have so far to deal with it is "TRIAL and ERROR" which is really really bad.

By the way, I figure out that the ".fr*" folders were created by "File Roller"

---

### Post by porchrat on 2008-08-31
With me most of the things I install have commons as well so I do a "sudo apt-get remove" for the program and the common.

---

### Post by porchrat on 2008-08-31
With me most of the things I install have commons as well so I do a "sudo apt-get remove" for the program and the common.

That generally completely removes the program, config files and all.

Sorry for the double post my browser did something really whacko there.

---

