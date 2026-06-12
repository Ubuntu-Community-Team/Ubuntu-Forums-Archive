---
title: "Updating?"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-02
What is the terminal command to update the OS or any app......

```
sudo- apt get update?
```

Thanks.

---

### Post by sidzen on 2012-10-02
[PHP]sudo apt-get update[/PHP] then [PHP]sudo apt-get upgrade[/PHP] or [PHP]sudo apt-get dist-upgrade[/PHP]Be careful with the latter.

This cannot be your first install, with over 1200 posts -- what's up?

---

### Post by Yezinki on 2012-10-02
Thanks sidzen, Which do you mean by latter?

```
sudo apt-get upgrade  
```


OR 


```
sudo apt-get dist-upgrade  
```

Yes I was away for about 4 plus years doing research on Cancer cure treaments, now back to square 1.........

---

### Post by vasa1 on 2012-10-02
> **Yezinki said:**
> ... Yes I was away for about 4 plus years doing research on Cancer cure treaments, now back to square 1.........

I wish all is well with you now but do try to make your thread titles more informative. It will help you and others.

---

### Post by sidzen on 2012-10-02
[PHP]sudo apt-get dist-upgrade[/PHP] -- it may cause problems on older machines by, say, installing an incompatible newer kernel.  

After a new install and with all functioning as it should, I prefer to first install aptitude and mc right after the update

[PHP]sudo apt-get install mc aptitude[/PHP]then
[PHP]sudo aptitude safe-upgrade[/PHP]  and using mc as root to edit the sources.list file
[PHP]sudo mcedit /etc/apt/sources.list[/PHP]   as desired -- best wishes!

---

### Post by Yezinki on 2012-10-02
Thanks sidzen & vasa1 for showing your concern.

I am grateful to all experienced memebers like ya who are helping me start again.

Its a fresh install with updating.

Installed G Chrome & Chromium browser too.

Now in which order should the commands be?

---

### Post by jerrrys on 2012-10-02
> **Yezinki said:**
> Yes I was away for about 4 plus years doing research on Cancer cure treaments, now back to square 1.........

Your public profile says retired

---

### Post by Yezinki on 2012-10-02
Yes it does........offically retired not working for hospitals any more only research & consultancy now.......

---

### Post by grahammechanical on 2012-10-03
> Now in which order should the commands be?

first we need to update the package lists to identify the differences between the packages on our machine and those on the server/repositories. Then we need to run the upgrade to change those packages that have been upgraded in the repositories.

so, it is

```
sudo apt-get update
```

followed by

```
sudo apt-get upgrade
```

Regards.

---

### Post by Yezinki on 2012-10-03
Thanks grahammechanical for your reply & posting terminal commands.

---

