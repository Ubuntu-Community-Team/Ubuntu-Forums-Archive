---
title: "HOWTO: Fix the &quot;Firefox taking up the whole screen problem&quot;"
date: 2008-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Crafty Kisses on 2008-11-14
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```

Once you've done that close out CCSM, then open CCSM back up again, then change that to:
```
any
```

Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```

I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal. The issue really only occurs when Firefox crashes and you reboot it, but those are the fixes and I've tested them myself and they do actually work.

---

