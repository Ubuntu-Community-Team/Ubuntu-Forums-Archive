---
title: "Python WindowsError Exception"
date: 2010-07-19
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-07-19
Ey fellas,

I have made a script that makes a replica of a target file/folder at a designated location and will poll every x seconds(specifiable by the user) to see if the original file has changed, if so it will overwrite the file at the target path with the original file/directory. I have been using this on my server to do a semi-live backup of all server logs to an external hard drive over the network. The only problem is that if the network goes down for some reason I get WindowsError like so:

```

WindowsError: [Error 53] The network path was not found: 'M:Archive\\Logs'//...

```

I know I have to use a try/except block but would I use WindowsError to catch in the case that the path is not reachable, or is there a better exception to use? I am making this script to be compatible with Windows, Unix, and Mac systems so for the latter would I have to tack on an extra exception like so?

```

try: 
    //...
except WindowsError: //for Windows platform
    //...
except OSError: //for Unix/Mac platforms
    //...

```

Any help appreciated, thanks!

---

### Post by Bachstelze on 2010-07-19
The WindowsError exception is raised, so yes, that's the one you need to catch...

---

