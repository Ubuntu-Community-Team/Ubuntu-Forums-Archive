---
title: "Chromium randomly crashes on 12.04LTS"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by techbuntu27 on 2012-10-26
So I'm bothered with this problem I'm having for a couple of days from the time I installed Ubuntu 12.04LTS done a fresh install to my 2nd HDD. So I am currently using "Chromium Version 20.0.1132.47 Ubuntu 12.04 (144678)" I think its the current version which I downloaded straight from ubuntu software.

So yeah it keeps on crashing just random w/o any errors that pop-ups or notifications regarding the crash. I really need help on this.

---

### Post by CaptainMark on 2012-10-26
Its not a bug I've experienced or heard of and I've been using chromium for a long time on linux, 3 things you can do: 
1) Disable any unnecessary extensions - the most common thing to cause chrome or chromium to crash is poorly written extensions, disable all extensions and see if that helps, if it does re-enable them one by one until you identify the bad one
2) Delete your config files - If theres a config file that is causing problems with chromium then delete it, open a file browser and press ctrl+H to view hidden folders, navigate to /home/((user))/.config and delete the folder chromium be warned though this will erase all of your bookmarks and passwords unless you have them synced to your google account
3) update chromium - you're using the most up to date version of chromium in the software centre but this is in fact out of date open a terminal from the dash and copy and paste the following ```
sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt-get install chromium-browser
```this will update you to version 22,

If after all this it still doesn't work you should remove chromium and reinstall it, but in my experience this does very little. 
Your last resort would be to open a terminal from the dash and type chromium-browser, then continue to browse until the crash happens and then post the output back on here using code brackets, this means highlight the code and use the # button above to wrap text in code tags

---

### Post by techbuntu27 on 2012-10-27
Thank you very much for these informative instructions and I will certainly do your suggestions and will reply back if this will solve the problem.

Thanks!

---

