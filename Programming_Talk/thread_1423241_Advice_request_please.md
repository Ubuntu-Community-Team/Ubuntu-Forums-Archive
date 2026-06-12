---
title: "Advice request please"
date: 2010-03-06
forum: Programming Talk
---

### Post by Net_Resident on 2010-03-06
Hello all, I'm completely out of my depth on this topic so if any questions, please ask. I'll try to initially keep this as simple as possible. My initial goal is to just get advice for where to go to get appropriate advice, what questions I should be asking and what nomenclature applies to my questions.

On another forum with a old custom engine, I have a problem with some users posting large volumes of text that are irrelevant to any given topic. What I want to be able to do is to place the body of their text in either a collapsible panel of some type or add in some sort of vertical scrolling that is a fixed height.

I know that this forum for example has such a built in feature but the other forum does not. My very rudimentary knowledge leads me to believe that I could use some sort of custom CSS style sheet script to accomplish this.

I have no need to reinvent the wheel here so if there was a Firefox add on or some public release of any kind of script that would suit my need, that would be great. I did download the Firefox add on called Remove it Permanently but I don't think that will serve my purpose.

Should anyone like to see the forum I'm referring to, this is it.

 [http://vnboards.ign.com/](http://vnboards.ign.com/) You can easily drill down to any thread from there.

Thanks folks

---

### Post by GregBrannon on 2010-03-06
I think you want to ask your question in "Forum Feedback and Help."  I don't really understand your questions or what you're looking for, but I can't see the connection to Programming.

Mod, please move?

Good luck.

---

### Post by iMisspell on 2010-03-06
css would be something like this...

```

.ClassNameOfTableCell{
    width: 650px;

    overflow:auto;

    overflow-y: visible;

    line-height: 100%;
}

```

That will controll horizontally, you will have to change it to control vertically. **y** = horizontally **x** = vertically.


_

---

### Post by lisati on 2010-03-06
If you have moderator privileges on the other forum, you might want to look at reviewing the rules with other moderators.

---

### Post by Net_Resident on 2010-03-06
Thanks everyone :)

I'll mark this as solved but if someone has a tip, feel free to post it. I'll continue to check the thread. I believe I found the right tool and forum for the help I need. Greesemonkey and [http://userscripts.org./forums](http://userscripts.org./forums)

---

