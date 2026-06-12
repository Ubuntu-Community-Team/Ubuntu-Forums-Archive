---
title: "Android Development with Net beans"
date: 2008-08-24
forum: Programming Talk
---

### Post by sefs on 2008-08-24
I've got installed...

Sun Java 6 
Netbeans 6.5 Beta
Android Plugins
Android SDK 0.9 beta

But I cannot get the examples to build and run....

I am following this guide...

[http://wiki.netbeans.org/IntroAndroidDevNetBeans](http://wiki.netbeans.org/IntroAndroidDevNetBeans)

and getting this build error

***
init:
deps-jar:
ERROR: Unknown command 'compile'
Android Asset Packaging Tool

Usage:
 aapt l[ist] [-v] [-a] file.{zip,jar,apk}
   List contents of Zip-compatible archive.

 aapt d[ump] WHAT file.{apk} [asset [asset ...]]
   permissions      Print the permissions from the APK.
   resources        Print the resource table from the APK.
   configurations   Print the configurations in the APK.
   xmltree          Print the compiled xmls in the given assets.

 aapt p[ackage] [-f][-u][-m][-v][-x][-M AndroidManifest.xml] \
        [-I base-package [-I base-package ...]] \
        [-A asset-source-dir] [-P public-definitions-file] \
        [-S resource-sources] [-F apk-file] [-J R-file-dir] \
        [raw-files-dir [raw-files-dir] ...]

   Package the android resources.  It will read assets and resources that are
   supplied with the -M -A -S or raw-files-dir arguments.  The -J -P -F and -R
   options control which files are output.

 aapt r[emove] [-v] file.{zip,jar,apk} file1 [file2 ...]
   Delete specified files from Zip-compatible archive.

 aapt a[dd] [-v] file.{zip,jar,apk} file1 [file2 ...]
   Add specified files to Zip-compatible archive.

 aapt v[ersion]
   Print program version.

 Modifiers:
   -a  print Android-specific data (resources, manifest) when listing
   -c  specify which configurations to include.  The default is all
       configurations.  The value of the parameter should be a comma
       separated list of configuration values.  Locales should be specified
       as either a language or language-region pair.  Some examples:
            en
            port,en
            port,land,en_US
       If you put the special locale, zz_ZZ on the list, it will perform
       pseudolocalization on the default locale, modifying all of the
       strings so you can look for strings that missed the
       internationalization process.  For example:
            port,land,zz_ZZ
   -d  one or more device assets to include, separated by commas
   -f  force overwrite of existing files
   -j  specify a jar or zip file containing classes to include
   -m  make package directories under location specified by -J
   -u  update existing packages (add new, replace older, remove deleted files)
   -v  verbose output
   -x  create extending (non-application) resource IDs
   -z  require localization of resource attributes marked with
       localization="suggested"
   -A  additional directory in which to find raw asset files
   -F  specify the apk file to output
   -I  add an existing package to base include set
   -J  specify where to output R.java resource constant definitions
   -M  specify full path to AndroidManifest.xml to include in zip
   -P  specify where to output public resource definitions
   -S  directory in which to find resources
   -0  don't compress files we're adding
/home/pokeymon/hd2/data/programming/MyFirstAndroidApp/nbproject/build-impl.xml:334: exec returned: 2
BUILD FAILED (total time: 0 seconds)
***

What could be wrong.

Thanks.

---

### Post by Thorindb on 2008-08-24
I am having the exact same problem only difference being that I am using netbeans 6.1.  My belief is that the android plugin was created sometime ago and the android SDK has been modified significantly since then?  If someone has a work around I would be most appreciative.

---

### Post by sefs on 2008-08-24
> **Thorindb said:**
> I am having the exact same problem only difference being that I am using netbeans 6.1.  My belief is that the android plugin was created sometime ago and the android SDK has been modified significantly since then?  If someone has a work around I would be most appreciative.

I found this... [http://code.google.com/p/idea-android/wiki/GettingStarted](http://code.google.com/p/idea-android/wiki/GettingStarted)

but I could not get the very last suggestion to work, maybe you may have better luck.

Do you know if they are any newer plugins?

---

### Post by tinny on 2008-08-25
You know of the Eclipse plug-in, right?

Update site:

[https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)

This seems to be the development environment that Google are putting their weight behind. (Ive used it and its solid)

---

### Post by sefs on 2008-08-25
So no netbeans love i take it.
p.s. your link seems to be broken.  Giving a 404.

---

### Post by tinny on 2008-08-25
> **sefs said:**
> So no netbeans love i take it.
p.s. your link seems to be broken.  Giving a 404.

Are you talking to me?

I think that both NetBeans and Eclipse are great. IMO Eclipse has the better Android Development support.

---

