---
title: "libnotify show() makes system hang!"
date: 2008-12-16
forum: Programming Talk
---

### Post by legends2k on 2008-12-16
Hi,
I wrote a small GTK+ app. where I have a text box & a button. When I type something in the text box and click the button, I call *notify_notification_show()* and it works perfectly fine.
Then I added code for X server to give me a callback on a hotkey press. When I get the callback, I get the current system selection and make a call to *notify_notification_show()* which shows the current the selection as notification. This too works fine.

The problem is when I select the text in my own text box and press the hotkey combo, the whole system hangs for about 5 secs and then I see the notification. And the return value of notify_notification_show() is FALSE with **error message:**  *"Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."*

I am confused greatly since in all other windows, when I select text and press the combo it works, but in my own Gtk+ window it hangs and puts up fuss :confused: Please help.

---

