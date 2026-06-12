---
title: "yahoo problem"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by allarmguy on 2008-07-22
I have a problem with my yahoo mail account.When I`m opening my mail the firefox closes.If I open the messenger nothing happens.Can I will be able to get mail again with firefox?I try to use opera works with mail but don`t work with messenger because has not installed flash player and I can install it.Please anyone help me.:(

---

### Post by SunnyRabbiera on 2008-07-22
What opera version are you running?
and do you have flashplugin-nonfree?

---

### Post by kdb424 on 2008-07-22
That happened to me, then I updated and it's all fixed for me. If you havn't yet, try that. Then again, I get all beta updates too...

---

### Post by allarmguy on 2008-07-22
I have opera 9.51

---

### Post by tech0007 on 2008-07-22
Or you can recreate your firefox profile:

mv ~/.mozilla ~/.mozilla.bak

then open firefox.

---

### Post by allarmguy on 2008-07-22
when I make the update I can`t do a full update,I get only partial update.

---

### Post by allarmguy on 2008-07-22
how can I do that?were?OK try it don`t work

---

### Post by tech0007 on 2008-07-22
> **allarmguy said:**
> when I make the update I can`t do a full update,I get only partial update.

Try this on the terminal:

sudo apt-get update
sudo apt-get upgrade

To see the errors when firefox closes on your yahoo account, run firefox in the terminal and post the output here.

---

### Post by allarmguy on 2008-07-22
I allready do that but nothing...about full update.I have 0 packages to remove,0....

---

### Post by chrisod on 2008-07-22
Sounds like a flash issue to me. I mostly solved my flash problems by upgrading to the Flash 10 beta that is available on Adobe.com. They may have even gone gold with Flash 10 by now.

---

