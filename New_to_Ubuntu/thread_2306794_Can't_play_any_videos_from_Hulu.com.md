---
title: "Can't play any videos from Hulu.com"
date: 2015-12-18
forum: New to Ubuntu
---

### Post by Steve_Aita on 2015-12-18
Hello all, I'm running the latest version of Ubuntu on a laptop (Dell Inspiron E6420). I joined Hulu but I keep getting an error message that tells me to make sure that HAL is installed and tells me how to install it, which I do, and in terminal it tells me HAL isn't available any more. It tells me to try Firefox but that won't work either nor does Opera. I know its not the laptop because I was running Windows 10 and Hulu worked just fine. Please HELP!!!! Thanks for the help in advance.

---

### Post by brian-mccumber on 2015-12-18
Maybe this article will help - [http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up](http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up)

---

### Post by SeijiSensei on 2015-12-19
I use [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") with Firefox to load Flash for Windows.  It works for Hulu,

```

sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
sudo pipelight-plugin --enable flash
sudo pipelight-plugin --create-mozilla-plugins

```

---

### Post by Steve_Aita on 2015-12-21
[COLOR=#000000]brian-mccumber, Thanks for your reply, I went to the link you provided and that fixed the problem in Firefox only, it still won't work in Google Chrome but it's at least working...Thank you very much for your help.
Steve Aita[/COLOR]

---

