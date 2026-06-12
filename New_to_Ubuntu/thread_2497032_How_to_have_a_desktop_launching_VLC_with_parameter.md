---
title: "How to have a desktop launching VLC with parameterss"
date: 2024-04-20
forum: New to Ubuntu
---

### Post by peterpan0011 on 2024-04-20
Hi everybody, thanks for your help
I need to have on my Desktop a launch file for VLC with an IP adress (Camera)

vlc rtsp://10.1.1.56:554

This command line works fine like this on Terminal
but when I put it as  EXEC=VLC rtsp://10.1.1.56:554, only vlc runs and I have not the video from my camera.
What am i doing wrong?
Thanks

---

### Post by MAFoElffen on 2024-04-21
> **peterpan0011 said:**
> 
```

EXEC=VLC rtsp://10.1.1.56:554

```

Try changing that to
```

Exec=sh -c "VLC rtsp://10.1.1.56:554"

```
That way it passes the whole command with the parameter list of what is contained within the quotation marks...

---

### Post by peterpan0011 on 2024-04-21
Thanks I'll try ASAP :P

---

