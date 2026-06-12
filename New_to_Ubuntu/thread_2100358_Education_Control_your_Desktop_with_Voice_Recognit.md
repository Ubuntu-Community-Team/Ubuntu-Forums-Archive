---
title: "Education: Control your Desktop with Voice Recognition *NEW*"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by honeybear on 2013-01-01
Hi,

(1)
I have been fascinated by my new Android, and what offers Google. There are positive things and drawbacks.

I am pleased to give you this script pa-voicerecognition.sh :


```

sh pa-voicerecognition.sh    #speak into your mic

sh pa-voicerecognition.sh --stop-rec   #to stop speaking
```


(2) Voice control of the desktop over openbox:

```


    <keybind key="W-Pause">
      <action name="Execute">
        <execute>   sh ~/.scripts/pa-voicerecognition.sh --cmdjs </execute>
      </action>
    </keybind>

    <keybind key="Pause">
      <action name="Execute">
        <execute>   sh ~/.scripts/pa-voicerecognition.sh --stop-rec </execute>
      </action>
    </keybind>


```


(3) Add your commands to this script at the end.

Enjoy the magic !!

---

