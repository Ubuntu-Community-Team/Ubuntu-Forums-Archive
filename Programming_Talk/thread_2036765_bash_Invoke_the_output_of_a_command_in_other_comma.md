---
title: "bash: Invoke the output of a command in other commands"
date: 2012-08-02
forum: Programming Talk
---

### Post by searchfgold6789 on 2012-08-02
Hi,
Here is what I'm trying to do. I have a command that prints lines of code: ```
echo -e "# RTL8188CUS wifi\nblacklist 8192cu\nblacklist rtl8192c_common\nblacklist rtlwifi"
``` and I would like to append the resulting code to the end of the file. The file is owned by root and the user is non-root, however.
Here is what I've tried:
```
sudo echo -e "# RTL8188CUS wifi\nblacklist 8192cu\nblacklist rtl8192c_common\nblacklist rtlwifi" >> file
```Results in permission denied.
```
echo -e "# RTL8188CUS wifi\nblacklist 8192cu\nblacklist rtl8192c_common\nblacklist rtlwifi" >> sudo sed -i file
``` results in sed error.
Any advice on how to properly do this?
I was thinking about including the echo command in the sed command but I have no idea how to do that.

---

### Post by steeldriver on 2012-08-02
you can use 'tee'

```
echo -e "stuff\nmore stuff\neven more stuff" | sudo tee -a *file*
```

---

