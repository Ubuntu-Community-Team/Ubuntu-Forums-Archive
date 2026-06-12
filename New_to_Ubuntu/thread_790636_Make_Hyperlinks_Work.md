---
title: "Make Hyperlinks Work"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by nullomodo on 2008-05-11
Hi Everyone.
I have been using ubuntu for a while now, upgraded to hardy when it was released.
Hardy came with Firefox 3 - which was bugging the life out of me, system freezing the works. I uninstalled Firefox 3 and installed Firefox 2 but now hyperlinks in Thunderbird and documents don't work. I have looked at System>Preferences>Preferred Applications and Firefox is not in the list. There is a custom command field and I have tried firefox %s and firefox-2 %s and it still doesn't work!
Can anyone help me?
Thanks

---

### Post by smoker on 2008-05-11
did you restart the desktop after installing firefox 2?

anyway, try the custom command 'mozilla-firefox' or 'mozilla-firefox %' and see if any of those work,

best of luck

---

### Post by 1richard on 2008-05-13
Here is what I did
   1. Open Thunderbird version 2.0.0.14
   2. Go to the Edit menu
   3. Click on Preferences
   4. Click the Advanced tab
   5. Click the Config Editor button.
   6. An about:config window will open up.
   7. In the Filter box, enter network.protocol-handler.app.http
   8. If the editor is unable to locate it, create a new string and input network.protocol-handler.app.http.
   9. Enter firefox for the string value.
  10. Close out and restart Thunderbird.

Hyperlinks should now be available in your email!

got this from [http://itadmins.org/](http://itadmins.org/)

---

### Post by nullomodo on 2008-05-13
Hi 1richard
That worked perfectly!
I can now get hyperlinks from my emails to work!
smoker - tried all the custom commands I could think of, restarting in between and it still doesn't work - I guess it will sort itself when I upgrade to firefox 3 once it is stable.

Thanks both for your help!

---

