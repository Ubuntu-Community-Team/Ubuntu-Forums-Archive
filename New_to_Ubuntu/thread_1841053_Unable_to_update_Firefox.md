---
title: "Unable to update Firefox"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by eclipsechasers2 on 2011-09-08
Update manager said there were firefox updates, but it failed (didn't capture error messages). Went into Synaptic, which also failed - error messages are below. My internet connection is clearly working (it's how I'm posting this message), so I am unsure what needs to be done.


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_all.deb)
  404  Not Found [IP: 91.189.92.167 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-he_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-he_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_all.deb)
  404  Not Found [IP: 91.189.92.167 80]

---

### Post by snip3r8 on 2011-09-08
Have you tried choosing a different download server? the server you are downloading from may be dead.

---

### Post by eclipsechasers2 on 2011-09-08
Thanks. Changing from "server for US" to "main server" did indeed solve my problem.

---

### Post by snip3r8 on 2011-09-08
Glad to have helped,please remember to mark your thread as solved

---

