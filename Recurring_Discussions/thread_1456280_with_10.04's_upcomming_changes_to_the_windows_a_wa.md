---
title: "with 10.04's upcomming changes to the windows a way to fix it"
date: 2010-04-16
forum: Recurring Discussions
---

### Post by 133794m3r on 2010-04-16
Since they're deciding to make Ubuntu more like MACOSX which is something i personally HATE how the MACOSX UI is, it's one of the biggest reasons why i shall never use that OS ever again. I had to use it when i was in elementary school and have never looked back at it. But with 10.04 they are moving the window control buttons over to the other side where they are in mac osx. I was wondering if there is already a fix for how to keep it the way that it was. 

I don't want to have to deal with that UI change as it's by far the most ridiculous thing that i've ever seen in my life. It's as if Ubuntu's main UI devs are trying to pull macosx devs whilst very quickly pushing away their biggest potential group of users. Those being the people who are used to windows. And as such, it should be an easy switch. But if you start switching up everything to make it look like mac osx i'm sure many people will see ubuntu as that, and the transition will be harder. I know for one, i shall not be behind this change to the window buttons and because of it, if there isn't a quick fix to get it back, i'll stick with 9.10 until there is one.

---

### Post by perham on 2010-04-16
> **133794m3r said:**
> Since they're deciding to make Ubuntu more like MACOSX which is something i personally HATE how the MACOSX UI is, it's one of the biggest reasons why i shall never use that OS ever again. I had to use it when i was in elementary school and have never looked back at it. But with 10.04 they are moving the window control buttons over to the other side where they are in mac osx. I was wondering if there is already a fix for how to keep it the way that it was. 

I don't want to have to deal with that UI change as it's by far the most ridiculous thing that i've ever seen in my life. It's as if Ubuntu's main UI devs are trying to pull macosx devs whilst very quickly pushing away their biggest potential group of users. Those being the people who are used to windows. And as such, it should be an easy switch. But if you start switching up everything to make it look like mac osx i'm sure many people will see ubuntu as that, and the transition will be harder. I know for one, i shall not be behind this change to the window buttons and because of it, if there isn't a quick fix to get it back, i'll stick with 9.10 until there is one.

+1

I believe this is the most stupid decision ubuntu developers ever made. it is very uncomfortable and it really looks ugly.

---

### Post by Elfy on 2010-04-17
Moved to recurring discussions.

---

### Post by asddf on 2010-04-17
don't really think it makes any difference.

---

### Post by wilee-nilee on 2010-04-17
It's just to bad you can't customize it yourself.

---

### Post by Didius Falco on 2010-04-17
To move the window buttons back to the left, enter the following in a Terminal window **without** sudo:

```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
```

If you prefer the buttons in a different order, change them around - just keep them to the left of the ":".

Another way to do it is to install **Ubuntu Tweak**. It has a GUI way to change it under **Desktop**, **Window Manager Settings**.

---

### Post by k3lt01 on 2010-04-17
> **wilee-nilee said:**
> It's just to bad you can't customize it yourself.Ummm, you can. just read the post after yours. btw this method and others have been common knowledge within the Lucid discussions for ages. It pays to keep up to date with what's going on.

---

