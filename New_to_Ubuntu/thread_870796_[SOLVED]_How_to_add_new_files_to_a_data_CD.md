---
title: "[SOLVED] How to add new files to a data CD?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-26
I have a data CD, which I've previously maintained in Windows.
When I load it in Ubuntu, the data CD seems perfectly OK; all files are present and readable in Ubuntu.

Now, I want to add some new files to the CD.
How do I do that?

I tried Brasero (as it comes default with Ubuntu). However, I can't figure out how to write the new data files to the CD.

Either:

[LIST]
[*]Where is the documentation for Brasero, so that I can figure out how to use it? Or:
[*]Is there another program that you'd recommend for doing this?
[/LIST]
Thanks

---

### Post by stalkingwolf on 2008-07-26
you might give K3b a try.  if it is not installed you can find it
under Sound and Video in add & remove.

---

### Post by logos34 on 2008-07-26
Here's one guide (it's amazing how pathetic the documentation on brasero is):

[http://beginlinux.com/index.php/desktop_training/ubuntuhardyheron_cat/112-ubuntu804/908-braserobruner](http://beginlinux.com/index.php/desktop_training/ubuntuhardyheron_cat/112-ubuntu804/908-braserobruner)

Be sure to check the multisession option box if you want to be able to add to the disc later, otherwise it will finalize it

But the previous poster is right--you should cnsider k3b as an alternative.  It's a bit more complicated becuase of all the options, but it's the best burner

---

### Post by brian_p on 2008-07-26
> **Paddy Landau said:**
> 

[LIST]
[*]Is there another program that you'd recommend for doing this?
[/LIST]


The dvd+rw-tools package.

```
growisofs -M /dev/cdrom file_to_add
```

if you are comfortable with the command line.

---

### Post by Paddy Landau on 2008-07-26
> **stalkingwolf said:**
> you might give K3b a try.  if it is not installed you can find it under Sound and Video in add & remove.
Thanks for this. I installed k3b through Synaptic Package Manager.

I find it easier to understand than Brasero.

However...

K3b complained that I didn't have the Rock Ridge extensions. As a result (so I understand from the message), all the file names already on the CD show as indecipherable squiggles. This happens even though:

[LIST=1]
[*]The description in Synaptic Manager says that k3b includes Rock Ridge;
[*]Nautilus easily reads the CD with its file names.
[/LIST]
Do you know how I can solve this problem? I don't find Rock Ridge anywhere in Synaptic Manager (perhaps I've looked in the wrong places).

---

### Post by brian_p on 2008-07-26
> **Paddy Landau said:**
> 

K3b complained that I didn't have the Rock Ridge extensions. As a result (so I understand from the message), all the file names already on the CD show as indecipherable squiggles. This happens even though:

[LIST=1]
[*]The description in Synaptic Manager says that k3b includes Rock Ridge;
[*]Nautilus easily reads the CD with its file names.
[/LIST]
Do you know how I can solve this problem? I don't find Rock Ridge anywhere in Synaptic Manager (perhaps I've looked in the wrong places).

A data cd has an ISO 9660 file system on it. The Rock Ridge extensions to the ISO 9660 standard allow for file information specific to unix systems to be supported and included in the iso file made prior to being burned to the cd.

It could be the Windows application you used did not use Rock Ridge and I think it is not possible to add the extensions as an afterthought to the cd. Which is probably what k3b is complaining about.

One solution would be to copy the files off the cd and make a new one.

I'm unfamiliar k3b but I would have thought it still possible to add a file to the cd.

---

### Post by Paddy Landau on 2008-07-26
> **brian_p said:**
> One solution would be to copy the files off the cd and make a new one.
Thanks, I'll do that.

---

