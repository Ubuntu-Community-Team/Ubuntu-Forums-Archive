---
title: "Faster internet ?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Innernet on 2008-06-12
Do these tweaks really work ?

[http://www.youtube.com/watch?v=MTyatXvuuuo](http://www.youtube.com/watch?v=MTyatXvuuuo)

[http://www.youtube.com/watch?v=41GMPrCATas](http://www.youtube.com/watch?v=41GMPrCATas)

[http://www.youtube.com/watch?v=fp2PWJZFPSM](http://www.youtube.com/watch?v=fp2PWJZFPSM)

---

### Post by alienexplorers on 2008-06-12
In the ~/.mozilla/firefox/*.default directory add the data below to a file called user.js:
> terminator@terminator-desktop:~/.mozilla/firefox/mz9pt95b.default$ cat user.js
user_pref("security.warn_entering_secure", false);
user_pref("security.warn_entering_weak", false);
user_pref("security.warn_leaving_secure", false);
user_pref("security.warn_submit_insecure", false);
user_pref("security.warn_viewing_mixed", false);
user_pref("signed.applets.codebase_principal_support", true);
user_pref("network.dns.disableIPv6", true);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("ui.submenuDelay", 0);
user_pref("image.animation_mode", "none");
user_pref("dom.max_script_run_time", 15);
user_pref("content.max.tokenizing.time", 3000000);
user_pref("content.notify.backoffcount", 5);
user_pref("content.notify.interval", 1000000);
user_pref("content.notify.ontimer", true);
user_pref("content.switch.threshold", 1000000);
user_pref("content.maxtextrun", 4095);
user_pref("nglayout.initialpaint.delay", 1000);
user_pref("network.http.max-connections", 10);
user_pref("network.http.max-connections-per-server", 16);
user_pref("network.http.max-persistent-connections-per-proxy", 16);
user_pref("network.http.max-persistent-connections-per-server", 4);
user_pref("DOM.disable_window_status_change", true);
user_pref("plugin.expose_full_path", true);
user_pref("browser.enable_automatic_image_resizing", true);
user_pref("plugin.expose_full_path", true);
user_pref("sessionsaver.settings.autoload", true);


---

### Post by Najand on 2008-06-12
"FasterFox" plugin for firefox does all those for you.

---

### Post by pjnsmb on 2008-06-12
Fasterfox does not work on Firefox 3  .

Try Swiftweasel

---

### Post by Ripfox on 2008-06-12
Or iceweasel

---

### Post by cariboo on 2008-06-13
Has anybody noticed the screen that pops up when you type about:config in the latest version of firefox?

See the attachment:

---

### Post by Bubba64 on 2008-06-13
Go here
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)
and you can force the install of fasterfox, also add nightly tester tools from Mozilla add ons to force the other add ons you may have hat are not compatible with FF 3.

---

