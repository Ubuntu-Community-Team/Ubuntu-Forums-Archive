---
title: "Ubuntu Software Center not Loading"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2012-02-27
I'm running Xubuntu 11.10 on a Dell Dimension 4400.
Whenever I try and open the Ubuntu Software Center, it does, but the window just stays gray:
[IMG]http://i.imgur.com/oikjQl.png[/IMG]
And it'll just sit there, like that, until I try and close it, and then it'll say that Ubuntu Software Center isn't responding, and I just have to force shut it.

Anyone know what's up with this?

---

### Post by cortman on 2012-02-27
Don't know what's making it do that (USC is notoriously flaky at times), but the do-all fix for it is to uninstall and reinstall.

```
sudo apt-get remove software-center
sudo apt-get install software-center
```

I've helped many people try and troubleshoot the USC, and so far uninstallation/reinstallation is the only reliable fix I've found.

---

### Post by DaimyoKirby on 2012-02-27
Ok, I'll give it a shot. It removed xubuntu-desktop, though. What would be the command to install the desktop without installing all the recommended packages (such as abiword, gnumeric, all the ones that I removed)?

---

### Post by donkyhotay on 2012-02-27
The desktop package is a meta package that doesn't do anything itself so it's not necessary. Basically it's a way of more easily installing all the original software the system came with without having to pick and choose each one by itself.

---

### Post by DaimyoKirby on 2012-02-27
@Donkyhotay - Ok, so I suppose I won't worry about that then, and just not install it.

@Cortman - I'm still having the same issue, but technically I can install everything through the command prompt (as long as I know what I want), can't I?

---

### Post by wildmanne39 on 2012-02-28
Hi, yes you can and I recommend installing synaptic package manager and see if that works it is actually a better package manager in my opinion.
```
sudo apt-get install synaptic
```
Thanks

---

### Post by cortman on 2012-02-28
+1 to Synaptic. It's a world-class GUI package manager, if you prefer such. I personally do all my installing via the command line, but if you need to look up package information, use Synaptic.

---

### Post by DaimyoKirby on 2012-03-02
Ok, thanks.
I suppose Synaptic is better, I just like USC because it's easier to just browse and read about programs. More visually appealing, I suppose. But I'll just use Synaptic and Terminal from now on.
Thanks again.

---

### Post by cortman on 2012-03-02
> **DaimyoKirby said:**
> Ok, thanks.
I suppose Synaptic is better, I just like USC because it's easier to just browse and read about programs. More visually appealing, I suppose. But I'll just use Synaptic and Terminal from now on.
Thanks again.

I know just what you're saying about the USC- it really is a beautiful app and when it works it works wonderfully. I would uninstall it and reinstall if I were you. The visuals and smoothness of experience are about enough to make it worth it.
But it's your choice. Good luck!

---

### Post by Krytarik on 2012-03-02
> **DaimyoKirby said:**
> I just like USC because it's easier to just browse and read about programs. More visually appealing, I suppose.
Then just give this a shot:
```
rm -r ~/.cache/software-center
```Btw., you shouldn't mark a thread as "solved" if the matter it's about isn't really solved; simply using another package manager is *not* a valid solution. ;-)

Hope that works.

---

### Post by luchesar on 2012-09-17
> **Krytarik said:**
> Then just give this a shot:
```
rm -r ~/.cache/software-center
```Btw., you shouldn't mark a thread as "solved" if the matter it's about isn't really solved; simply using another package manager is *not* a valid solution. ;-)

I had exactly the same symptoms, and, at least for me, removing the cache solved the problem. Thanks, **Krytarik**!

---

### Post by romanrogue on 2012-10-13
This solution worked for me as well. However I love to learn, how exactly did this fix help? I know the rm command is to delete a file, but why was this file a problem?

---

### Post by luchesar on 2012-10-13
> **romanrogue said:**
> This solution worked for me as well. However I love to learn, how exactly did this fix help? I know the rm command is to delete a file, but why was this file a problem?

When used with the **-r** option, **rm** acts recursively; that is, it removes not just a single file, but a whole directory tree. In this case, the complete contents of the **~/.cache/software-center/** directory are removed. From what I can tell, it holds the per-user cache of the Software Center application. That cache is a database and databases can become corrupt -- sometimes to such extent that applications simply crash or hang as they are unable to handle the corruption. Because this database is used just to speed the things up, it's safe to remove it so it can be rebuild from scratch.

Well, take this explanation with a grain of salt, as I've not bothered to check the details, but I guess that at least the overall picture is correct.

Cheers,
Luchesar

---

