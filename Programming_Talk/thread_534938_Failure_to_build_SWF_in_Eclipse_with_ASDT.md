---
title: "Failure to build SWF in Eclipse with ASDT"
date: 2007-08-25
forum: Programming Talk
---

### Post by sgartner on 2007-08-25
I am running  Eclipse 3.2.2 under Ubuntu 7.04 and have installed the Actionscript Development Tool (ASDT) plug-in via the Eclipse Update Manager.

The installation was clearly successful and I now have the ActionScript2 options under the Eclipse preferences and can successfully create ActionScript projects in Eclipse.

I have ActionScript code hinting when working in Eclipse and see that the base ActionScript classes are stored at under /usr/lib/eclipse/plugins/....

In Eclipse under Preference/ActionScript2/Complier I have the default MTASC selected.

The project properties are defaults with the output SWF listed as Test.swf to be created in bin under the project root folder.

I have single class in my project (Test.as) with a main method that calls the constructor to create an instance of itself.

When I do a build in in Eclipse, I get no error messages, but alas no SWF is produced.

I am running eclipse from my user account, but installed the ASDT plug-in with eclipse running from root.

I have also installed MTASC separately via the package manager, as was Eclipse.

Is anyone able to shed any light on the steps that I need to take, or redo, to be able to create SWF's from Eclipse in Ubuntu.

Thanks for your efforts. steve

---

