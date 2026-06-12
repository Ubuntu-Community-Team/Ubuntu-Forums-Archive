---
title: "Thunderbird 17.0.4 quoted message problem"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by ben222qmz7 on 2013-03-25
Thunderbird 17.0.4 under Xubuntu 12.04
When I read usenet messages Thunderbird shows only the text
of the last mailer even if there are quotes of other mailers too.  There are only vertical lines on both sides where the text from others should be but no text.

The same thing happens when testsending normal mail to myself (and of course to everybody else). If I send a few lines of any text and then answer it  adding some moore lines. Then after receiving mail the original text is not there but only that added extra. The quoted text is always missing and that empty space with vertical lines only exists.

When looking at View/Message source the quoted message is there.

There is no difference if using Html or plain text.

What is wrong and what to do??

---

### Post by Krytarik on 2013-03-25
Make sure that the option "Edit -> Preferences -> Display -> Formatting -> Plain Text Messages -> When displaying quoted... -> Color" is not set to the same as the background color, which is white by default.

Found it here: [http://forums.mozillazine.org/viewtopic.php?p=7700145#p7700145](http://forums.mozillazine.org/viewtopic.php?p=7700145#p7700145)

Regards.

---

### Post by ben222qmz7 on 2013-03-26
So simple and so easy! Thanks very much!

---

