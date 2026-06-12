---
title: "Keyword substitution with bazaar in launchpad"
date: 2010-04-14
forum: Programming Talk
---

### Post by carandraug on 2010-04-14
I'm trying to get keyword substitution working with bazaar. I have my code in launchpad.

I've seen the [plugin for that in launchpad]("https://launchpad.net/bzr-keywords") but it's not in the [list of bazaar plugins]("http://wiki.bazaar.canonical.com/BzrPlugins"). However, the changelog of bazaar versions, says that it had support since version 1.4 through use of plugins (my version is 2.0.2). But does the plugin needs to be on the server (launchpad)?

I'm new to revision control systems. Can anyone point me on how to get it working?

Thanks in advance

---

### Post by carandraug on 2010-04-17
I never managed to get it working but here's how to install it. It's incredible how little information there's about it unless you go look into the code of the plugin.

[LIST=1]
[*]download the code from launchpad (you need bazaar for this)
```
bzr branch lp:bzr-keywords
```
[*]install the plugin (basically move the plugin code into the bazaar configuration folder)
```
mkdir ~/.bazaar/plugins/keywords
cp -R ./bzr-keywords/* ~/.bazaar/plugins/keywords

```
[*]test the plugin (you should get a reassuring message saying that a certain number of tests were passed. It's not good if it says that it passed all tests but the number of tests are 0)
```
bzr selftest keywords.tests
```
[*]configure bazaar to use the plugin. Open '~/.bazaar/bazaar.conf' and configure it according to:
```
bzr help keywords
```
[*]put whatever keywords you want in the files
[*]commit your code
[/LIST]

Seems there's some sort of [bug]("https://bugs.launchpad.net/bzr-keywords/+bug/408841") with the plugin so it didn't work for what I wanted. My workaround was from Ian Clatworthy in launchpad

[QUOTE=Ian Clatworthy]
I'd ignore the keywords plugin and use the version-info command. See [http://doc.bazaar.canonical.com/latest/en/user-reference/version-info-help.html]("http://doc.bazaar.canonical.com/latest/en/user-reference/version-info-help.html").

If Octave offers some API for getting the output of external commands AND you're always running the code from a branch or checkout, then I'd run `bzr version-info` each time to collect the revision number. Otherwise, I gather you have some sort of build process where the software gets packaged up and distributed to others? In that case, use something like
```

bzr version-info --template "VERSION = '{revno}'" > version.m
```

as you're building or packaging the software.[/QUOTE]

I decided to have octave run a system command to check the revision number
```
bzr_cmd                   = sprintf("bzr version-info");
[bzr_status, main.revno]  = system (bzr_cmd);
if (bzr_status != 0)
  error ("Error when checking revision number with command '%s'. Exit code was '%g'", brz_cmd, bzr_status)
endif
```

---

