---
title: "Java multi-page application - what is the best way"
date: 2011-12-21
forum: Programming Talk
---

### Post by kamaji792 on 2011-12-21
I'd like to know what is the best way to handle a Java application that has multiple pages/screens.

I'd like to have a main menu page/screen with a series of button that will jump to allow you to run various options.  I anticipate that having jumped to an option the most likely outcome would be to go back to the main menu page/screen.  Currently the only way I can find to do this is to use a CardLayout.  Then when I have finished with one page/screen I can easily switch to another.

Is there a better way of doing this?

Are there any examples?

Thanks in advance k

PS - I am using the NetBeans IDE.  Though I prefer to do my development just using **vim**

---

### Post by Zugzwang on 2011-12-21
Here is an easy way: Add a few JPanels to your Frame and customize the layout such that all Panels scale 100% in both dimensions. Then ensure that in every time instant, only one of them is visible (setVisible(true)/setVisible(false)). This way, you can switch between the JPanels. Then, put whatever you like for your screens on the JPanels.

---

### Post by kamaji792 on 2011-12-23
> **Zugzwang said:**
> Here is an easy way: Add a few JPanels to your Frame and customize the layout such that all Panels scale 100% in both dimensions. Then ensure that in every time instant, only one of them is visible (setVisible(true)/setVisible(false)). This way, you can switch between the JPanels. Then, put whatever you like for your screens on the JPanels.

I'll give it a go.  I was aware of this option but for memory management, did not want to have all the panels up at the same time.  That said memory management is a small part of the issues I have.

Anyway thanks for the reply

k

---

