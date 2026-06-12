---
title: "Qt 4 Designer will no longer launch"
date: 2009-08-11
forum: Programming Talk
---

### Post by xaegis on 2009-08-11
Qt 4 designer was installed, and worked beautifully. I then installed assistant and linguist which had missing libs from the repositories. I installed all the missing libs and now those two work beautifully but Qt4 designer will no longer launch. The error message I'm getting is:
```

user@user:~$ designer-qt4
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/cache-user: Not a directory
trying to create local folder /home/user/.kde/cache-user: Not a directory
trying to create local folder /home/user/.kde/cache-user: Not a directory
trying to create local folder /home/user/.kde/cache-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
makekdewidgets(5964): Failed to lock file "/home/user/.kde/cache-user/kpc/kde-icon-cache.lock" , last result = 2 
makekdewidgets(5964): Couldn't create index file "/home/user/.kde/cache-user/kpc/kde-icon-cache.index" 
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
QMetaProperty::read: Unable to handle unregistered datatype 'QList<QChar>' for property 'KCharSelect::displayedChars'
QMetaProperty::read: Unable to handle unregistered datatype 'QList<QColor>' for property 'KColorCombo::colors'
Error while reparenting!
trying to create local folder /home/user/.kde/cache-user: Not a directory
trying to create local folder /home/user/.kde/cache-user: Not a directory
makekdewidgets(5964) KToolInvocation::klauncher: klauncher not running... launching kdeinit
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/tmp-user: Not a directory
trying to create local folder /home/user/.kde/share: Not a directory
trying to create local folder /home/user/.kde/socket-user: Not a directory
kdeinit4: Aborting. bind() failed: : Not a directory
Could not bind to socket '/home/user/.kde/socket-user/kdeinit4__0'



```


When I attempt to install or uninstall the program i get this message after a sucessfull install:
```

/usr/bin/mandb: only 8 fields in content
/usr/bin/mandb:  index cache /var/cache/man/4890 corrupt

```

Does anyone have any ideas about what might be going on?

Thanks in advance.

---

### Post by dwhitney67 on 2009-08-11
Yes, it would appear that /home/user/.kde is NOT a directory.

Check to see if this path exists, and if so, that it is a directory.  Perhaps at one time it was a directory, but you mistakingly altered its properties.

A quick spot check to perform is to open a terminal, and run the following command:
```

ls -al /home/user

```
Locate the ".kde" entry, if it exists, and verify that its permissions are (at a minimum):
```

drwxr-xr-x 4 user user 4096 ... .kde/

```
If not, correct the permissions with:
```

chmod 755 /home/user/.kde
chown -R user:user /home/user/.kde   # this may not be required

```
Of course, replace "user" as shown above with your actual user name.

P.S.  If /home/user/.kde does not exists whatsoever, then create it:
```

mkdir -m 755 /home/user/.kde

```

---

### Post by xaegis on 2009-08-11
Thanks! I thought it was a corrupted permissions issue, I changed the permissions on the .kde directory. And deleated the old file. (which had been turned into a gif of these two dudes btw) Now it launches but I am recieving a new error msg:

```

user@user:~$ designer-qt4
QMetaProperty::read: Unable to handle unregistered datatype 'QList<QChar>' for property 'KCharSelect::displayedChars'
QMetaProperty::read: Unable to handle unregistered datatype 'QList<QColor>' for property 'KColorCombo::colors'
Error while reparenting!
QMetaProperty::read: Unable to handle unregistered datatype 'ShortcutTypes' for property 'KKeySequenceWidget::checkForConflictsAgainst'
QMetaProperty::read: Unable to handle unregistered datatype 'KUrl' for property 'KUrlRequester::url'
QMetaProperty::read: Unable to handle unregistered datatype 'KFile::Modes' for property 'KUrlRequester::mode'
QMetaProperty::read: Unable to handle unregistered datatype 'KUrl' for property 'KUrlRequester::url'
QMetaProperty::read: Unable to handle unregistered datatype 'KFile::Modes' for property 'KUrlRequester::mode'
makekdewidgets(4198) Sonnet::Loader::loadPlugin: Successfully loaded plugin: "kspell_enchant.desktop"
makekdewidgets(4198) Sonnet::Loader::loadPlugin: Successfully loaded plugin: "kspell_hspell.desktop"
Enchant dict for "en_US" 0x1267540 
makekdewidgets(4198) Sonnet::DictionaryComboBox::reloadCombo: Populate combo: "" : "tr"
makekdewidgets(4198) Sonnet::DictionaryComboBox::reloadCombo: Populate combo: " (Australia)" : "en_AU"
makekdewidgets(4198) Sonnet::DictionaryComboBox::reloadCombo: Populate combo: " (Canada)" : "en_CA"
makekdewidgets(4198) Sonnet::DictionaryComboBox::reloadCombo: Populate combo: " (South Africa)" : "en_ZA"
makekdewidgets(4198) Sonnet::DictionaryComboBox::reloadCombo: Populate combo: " (United Kingdom)" : "en_GB"
makekdewidgets(4198) Sonnet::DictionaryComboBox::reloadCombo: Populate combo: " (United States of America)" : "en_US"
Designer: An error has been encountered at line 1 of /home/user/.designer/widgetbox4.5.xml: Start tag expected.


```

---

### Post by dwhitney67 on 2009-08-11
I have no idea what is causing the newest error that you are having.  You could consider removing the .designer directory to see if that allays the issue.  QtDesigner should recreate it for you.
```

rm -rf ~/.designer

```

---

