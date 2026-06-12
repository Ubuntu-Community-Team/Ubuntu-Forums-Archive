---
title: "Re: JaJavascript: a==b however c-a != c-b"
date: 2014-05-31
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2014-05-31
So i am trying to adjust a elements height on after resize/load
i figured why recalculate half the equation when it does not change, then it no longer resizes correctly but well *points at title*
so i stated trying to debug this and i am baffled, here is my debug alert
```
    alert(
        'window.innerHeight: '+window.innerHeight+'\n'+
        "getId('player').offsetHeight-30: "+(getId('player').offsetHeight-30)+'\n'+
        "playerHeight: "+(playerHeight)+'\n'+
        '\n'+
        "getId('player').offsetHeight-30==playerHeight: "+(getId('player').offsetHeight-30==playerHeight)+'\n'+
        "window.innerHeight-getId('player').offsetHeight-30==window.innerHeight-playerHeight: "+(window.innerHeight-getId('player').offsetHeight-30==window.innerHeight-playerHeight)+'\n'+
        '\n'+
        "window.innerHeight-getId('player').offsetHeight-30: "+(window.innerHeight-getId('player').offsetHeight-30)+'\n'+
        "window.innerHeight-playerHeight: "+(window.innerHeight-playerHeight)+'\n'+
        'window.innerHeight: '+window.innerHeight
    );
```
it gives me this
```
window.innerHeight: 864
getId('player').offsetHeight-30: 129
playerHeight: 129

getId('player').offsetHeight-30==playerHeight: true
window.innerHeight-getId('player').offsetHeight-30==window.innerHeight-playerHeight: false

window.innerHeight-getId('player').offsetHeight-30: 675
window.innerHeight-playerHeight: 735
window.innerHeight: 864
```
here are the screenshots
[IMG]http://i.imgur.com/Uzq3pl0.png[/IMG]
[IMG]http://i.imgur.com/PRrxjcP.png[/IMG]

---

### Post by Vaphell on 2014-06-01
```
window.innerHeight-getId('player').offsetHeight[COLOR="#FF0000"]-[/COLOR]30: 675
window.innerHeight-playerHeight: 735
```

too lazy to use parentheses? ;-)

---

### Post by pqwoerituytrueiwoq on 2014-06-01
that should not make a difference

80-10=70
80-6-4=70
80-(6-4)=oh wait, your right that would be 78

well now i feel like a idiot

---

