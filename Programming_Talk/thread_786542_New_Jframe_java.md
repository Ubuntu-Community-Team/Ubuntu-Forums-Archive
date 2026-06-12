---
title: "New Jframe java"
date: 2008-05-08
forum: Programming Talk
---

### Post by Geir102 on 2008-05-08
Hi i'm doing a GUI project in netbeans. And i have my main Jframe, any one know how i can get another one. Like when I press a button a new Jframe pops  
up.

---

### Post by Zugzwang on 2008-05-08
You can just instantiate any Frame and call the setVisible(true) method of it, just like it is done in the pre-generated main() method of a JFrame:
[PHP]
new YourFrame().setVisible(true);
[/PHP]

For making it open when you press a button, double click onto the "actionPerformed" event of the button and Netbeans will make a method (in the frame class) for you that is called when you press the button.

---

### Post by Geir102 on 2008-05-08
Ok thaks...just one more question. I see when i create a new Jframe its set up whit a main. Is it suppose to?

---

### Post by achelis on 2008-05-08
Depending on what you need it for it sounds like you might benefit from using a JDialog instead of a JFrame.

I'm not sure what you mean by it's set up with a main?

---

### Post by Zugzwang on 2008-05-08
> **Geir102 said:**
> Ok thaks...just one more question. I see when i create a new Jframe its set up whit a main. Is it suppose to?

Of course it is supposed to - otherwise Netbeans wouldn't do it. ;-) No, just kidding. The automatically included main(...)-function is just for convenience. It is good practice to delete it if it isn't needed.

---

### Post by Geir102 on 2008-05-08
thanks alott for the quick answers:)

---

