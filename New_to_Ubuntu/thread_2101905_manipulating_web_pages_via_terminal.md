---
title: "manipulating web pages via terminal"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by diabolusss on 2013-01-05
Hello! ):P

 I am searching for a way to manipulate content(functions, possibilities) of web pages using terminal(bash scripting). For example to log into [http://ubuntuforums.org](http://ubuntuforums.org) account, then read new posts and maybe post a new thread. I wasn't able to find any useful information, only how to get(wget; or send mail) not to post. It would be great if it's possible :D 

Thank you

---

### Post by sandyd on 2013-01-05
> **diabolusss said:**
> Hello! ):P

 I am searching for a way to manipulate content(functions, possibilities) of web pages using terminal(bash scripting). For example to log into [http://ubuntuforums.org](http://ubuntuforums.org) account, then read new posts and maybe post a new thread. I wasn't able to find any useful information, only how to get(wget; or send mail) not to post. It would be great if it's possible :D 

Thank you

I don't think this is possible, as posts are submited via HTTP POST.

However, there are some text-based browsers that you can use, mainly links2 and lynx

---

### Post by steeldriver on 2013-01-05
cURL?

[http://curl.haxx.se/](http://curl.haxx.se/)

---

### Post by tgalati4 on 2013-01-05
Dillo is another lightweight browser.  Since the source is available, you might be able to hook into one of the lightweight browsers to read posts and submit posts.  You are looking for an API to talk to and I am not aware of a vBulletin API that would let you talk to it directly.  But I am interested in what you come up with.  Brings me back to the BBS days--telephone modem bulletin board systems.

{{:;}} (ASCII popcorn)

---

### Post by diabolusss on 2013-01-06
i suspected that my idea might sound too crazy, however, thank you, everyone, for a clues. i'll try cURL and maybe something will come out of this xD

---

### Post by tgalati4 on 2013-01-06
Send a message ([http://ubuntuforums.org/sendmessage.php](http://ubuntuforums.org/sendmessage.php)) and ask them how you can interact with the forums through a text-based window.

---

