---
title: "Firefox 3.1 Shiretoko in 8.10 HELP NEEDED!"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by mjheagle8 on 2008-11-11
i wanted to install firefox 3.1, and was using minefield, but wanted the repository version. xulrunner 1.9.1 wouldnt install, so i got a different version from []("https://launchpad.net/~fta/+archive"). firefox 3.1 beta aka shiretoko then installed fine and works relatively well. however, it gives me an error when i try to use the search tool. i get this error:

Assertion failed:
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:ParamSubstitution(http://suggestqueries.google.com/complete/search?output=firefox&client=firefox&hl={moz:locale}&q={searchTerms},shire,[object Object])
5:SRCH_EURL_getSubmission(shire,[object Object])
6:SRCH_ENG_getSubmission(shire,application/x-suggestions+json)
7:getSubmission(shire,application/x-suggestions+json)
8:(shire,searchbar-history,null,[xpconnect wrapped nsIAutoCompleteObserver])


screenshot attached. please help me :) thanks. all help is appreciated.
-MH

sorry for smileys, forgot to turn them off.

---

