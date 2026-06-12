---
title: "Making a dialog box pop-up showing arbitrary text"
date: 2008-06-07
forum: Programming Talk
---

### Post by randysparks on 2008-06-07
Please be gentle with me because I'm not a programmer (beyond simple shell scripts). :(

Is there any shell command that causes a GTK+ dialog box pop-up showing some text and an OK button? There doesn't have to be anything happen when OK is clicked. It's literally an alert dialog.

---

### Post by smartbei on 2008-06-07
Check Zenity out: [http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by randysparks on 2008-06-07
> **smartbei said:**
> Check Zenity out: [http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

Just what I was looking for! Thanks.

Do you know if there's any other way of making a Zenity dialog box take input from a file, other than using the --text-info style of dialog box?

---

### Post by Yuzem on 2008-06-07
Some examples:
```
cat 'somefile' | zenity --text-info
```

```
cat 'somefile' | zenity --list --column ""
```

```
zenity --info --text "$(cat 'somefile')"
```

---

### Post by randysparks on 2008-06-08
> **Yuzem said:**
> Some examples:
```
cat 'somefile' | zenity --text-info
```

```
cat 'somefile' | zenity --list --column ""
```

```
zenity --info --text "$(cat 'somefile')"
```

Thanks but it should be pointed out that some of the dialog box types don't take piped input in this way. Perhaps the most useful, --info, won't. 

But the third example is just what I'm looking for.

---

