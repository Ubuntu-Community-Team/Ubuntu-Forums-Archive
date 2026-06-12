---
title: "Video downloads are saved as 'text' files"
date: 2016-06-06
forum: New to Ubuntu
---

### Post by kologha on 2016-06-06
Hi, I am using Ubuntu 14.04 but when I download and save a video clip, it is saved as a 'text' file. How can I stop this?
Regards

---

### Post by Impavidus on 2016-06-06
File extensions don't mean a lot in Linux. It's mostly about magic numbers embedded in the file to determine file types, but some applications make some use of extensions. You can freely change extensions by renaming the file. You can use the **file** tool to see what kind of file you've got. **file** uses a combination of magic number, extension and contents to guess the file type. In a terminal:```
file <filename>
```Instead of typing the filename, you can drag and drop the file into the terminal.

---

### Post by kologha on 2016-06-06
I'm afraid you have lost me! All I want to do is download a video clip using 'FlareGet'. I am not a computer geek and understand very little about using code. Can you please give me step by step instructions?
Regards

---

### Post by howefield on 2016-06-06
Can you give us an example of the video clips that you are downloading ?

Could well be a part download that "looks" like a text file, as I understand Flareget doesn't support resume so if you have had a broken download that might explain it.

---

### Post by kologha on 2016-06-06
[http://www.iomtt.com/News/2016/June/03/Round-up-of-qualifying-videos.aspx](http://www.iomtt.com/News/2016/June/03/Round-up-of-qualifying-videos.aspx)

[https://youtu.be/8Vxjc5VWjzk](https://youtu.be/8Vxjc5VWjzk)

The download is finished in about 10 seconds which is far too quick for a 3 minute clip. The downloaded file is 201 kb and it should be at least 30 mb. There are no settings on 'flareGet' which allow saving as a certain type, it seems as though you have to rely on the down-loader to determine the file type. I have tried a few other down-loaders and they also saved the video clips as 'text'. Last night I booted up WinXP (dual booting) and downloaded what I wanted using that but I don't wish to use XP on the internet because I don't trust it as far as virus' go. I had to do a clean reinstall of XP a month ago because of a virus and that's when I decided to start using Ubuntu but it's becoming a nightmare because I don't really understand the code side of Ubuntu!

---

### Post by vasa1 on 2016-06-06
Please check [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955) regarding this forum's policy about downloading content from YouTube.

---

### Post by kologha on 2016-06-06
If that means I am not allowed to download these video clips then I was not aware of it, and if that's the case then I will cease to download them.
Thanks for your help.
Regards.

---

### Post by col48 on 2016-06-07
The YouTube policy does not in itself mean you are not permitted to download video clips, but it _does_ mean you should make sure you have permission under the applicable licence from the owner of the clip.
If you are using Firefox, there is an Add-on (look under Tools menu for 'Add-ons' [at least for Firefox 46.0.1] and then Get Add-on) which adds a button in YouTube to download as MP4.

---

### Post by mastablasta on 2016-06-08
try video download helper add-on in Firefox. 
[SIZE=2]https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/
[/SIZE]

---

