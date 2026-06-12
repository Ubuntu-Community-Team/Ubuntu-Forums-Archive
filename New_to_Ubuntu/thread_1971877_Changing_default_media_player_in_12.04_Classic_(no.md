---
title: "Changing default media player in 12.04 Classic (no effects)"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Stunt Double on 2012-05-03
VLC just works better than Totem movie player on this computer. 
How can I make VLC the default player?
Thanks

---

### Post by mc4man on 2012-05-03
These 2 commands will set vlc as the default for most of the audio & video mimetypes vlc registers for (writes to ~/.local/share/applications/mimeapps.list 
Each is a long command, copy completely and paste into a terminal, press enter

 ```
grep "^MimeType=" /usr/share/applications/vlc.desktop | cut -d "=" -f 2   | xargs -d ';' -n 1 | grep -e "^video/" -e "^x-content/video"   | xargs -n 1 -I '{}' xdg-mime default vlc.desktop '{}'
```

```
grep "^MimeType=" /usr/share/applications/vlc.desktop | cut -d "=" -f 2   | xargs -d ';' -n 1 | grep -e "^audio/" -e "^x-content/audio"   | xargs -n 1 -I '{}' xdg-mime default vlc.desktop '{}'
```

Anything else not included you can set from the right click on filetype > properties > open with > set as default

---

### Post by papibe on 2012-05-03
Hi Stunt Double.

Run 'System Info' on the dashboard. Then under 'Default Applications' select VLC for Video.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Stunt Double on 2012-05-03
Problem solved!
Thanks to both of you for the help.

---

