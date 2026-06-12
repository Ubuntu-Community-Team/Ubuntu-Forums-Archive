---
title: "Get URL of firefox in ubuntu"
date: 2021-12-30
forum: New to Ubuntu
---

### Post by kilbha on 2021-12-30
Hi Community,

    I am new to ubuntu. I am trying to get current URL of firefox( can be any browser). I don't want to do any keyboard or mouse operations to do it. We can get current URL of browser by using xdotool. It will disturb the user because we will highlight URL and copy it. I want to get URL of browser by accessing browser. We can get same in windows, MacOS using .NET Automation and AppleScript respectively. How can we do it in ubuntu?

Thanks
Bhargav

---

### Post by schragge on 2021-12-31
See [Get URL of current active tab from Firefox via command line]("https://askubuntu.com/questions/929686") @Ask Ubuntu. The solution outlined there may require some adjustments, but you'll get the idea.

Instead of Python, I'd probably use [lz4jsoncat]("https://manpages.debian.org/unstable/lz4json/lz4jsoncat.1.en.html") and [jq]("https://stedolan.github.io/jq"). E.g.
```
sudo apt install lz4json jq
```
```
file="$HOME/.mozilla/firefox/[COLOR=darkgrey]<whatever-your-profile-is-named>[/COLOR]/sessionstore-backups/recovery.jsonlz4"
lz4jsoncat "$file"|jq -r '.windows[0].selected as $s|.windows[0].tabs[$s-1].entries|last.url'
```

Note that **.windows[].tabs[].lastAccessed** times (if you're going down that route) are in milliseconds while **date +%s** as well as **jq**'s builtin **now** give you time in seconds since the Unix epoch.

---

