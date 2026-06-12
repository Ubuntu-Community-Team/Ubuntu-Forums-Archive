---
title: "Problem with makefile error cs0009"
date: 2019-10-27
forum: New to Ubuntu
---

### Post by staibuz on 2019-10-27
[FONT=arial][COLOR=#101010]Hello,[/COLOR]
[COLOR=#101010]I'm a [/COLOR]newbie in [COLOR=#101010]Ubuntu and Linux use.[/COLOR]
[COLOR=#101010]I'm followed the instruction found on a Discussion on Steam to create a dll file and publish it in the workshop.[/COLOR]

below the instruction in detail:

[COLOR=#101010]I've followed all the point except the last (6. Creating a mod).[/COLOR]
When I launch the make/makefile command I recived an error.

```
error CS0009: Metadata file `/home/staibuz/Traduzione/ColossalManaged.dll' does not contain valid metadata
error CS0009: Metadata file `/home/staibuz/Traduzione/ICities.dll' does not contain valid metadata
error CS0009: Metadata file `/home/staibuz/Traduzione/Assembly-CSharp.dll' does not contain valid metadata
Compilation failed: 3 error(s), 0 warnings
Makefile:2: recipe for target 'Mod_Lang_IT.dll' failed
make: *** [Mod_Lang_IT.dll] Error 1
```

Here the instruction followed on Steam

[/FONT]```
[FONT=arial]Cities Skylines translation tools.[/FONT]
[FONT=arial] ----------------------------------



1. Introduction
---------------

Cities Skylines uses a proprietary file format for its language files. These
files are not human editable. Therefore, in order to translate the game into
more languages, tools are necessary to create and edit these files.

The library ColossalManaged.dll, that is shipped with Cities Skylines,
contains support to read and write .locale files. The consequence is that
it is almost a necessity to write tools in C#.

This package contains tools that allow you to convert from and to language
files. The tools are command-line tools, that must be run from a Windows
Command prompt or Linux shellj. I dislike GUI utilities because they cannot
be automated.

Translating consists of several steps:
   1. Convert an existing .locale file into a .po (gettext) file
   2. Edit the .po file
   3. Create a new .locale file from the original file and the .po file


2. Getting started
------------------

Extract this zip file in a directory and copy ColossalManaged.dll, into it. This
file comes with Cities Skylines and can be found in its installation directory.
Linux users will also have to install Mono. Most distributions contain Mono,
you can use zypper, yum or apt-get to install, i.e.:

zypper install mono

Dependencies have been avoided, so just the basic Mono installation is
sufficient.

3. Convert an existing .locale file into a .po (gettext) file
-------------------------------------------------------------

This is done with the tool locale2po. Open a command prompt or Linux shell and
cd to the directory where you have the tools available.

An example to convert the English locale file is:

Linux users:
    mono locale2po.exe -input en.locale -output en.po
Windows users:
    locale2po -input en.locale -output en.po

After executing the command the file en.po has been created.


4. Edit the .po file
--------------------

.po files are the GNU gettext format. The gettext format is a very common file
format for translating software. .po files can be edited with any text editor.
If you want to do this, open the .po file in a text editor and add your
translations to the msgstr lines. You have to leave the #. lines and the msgid
lines unmodified).

However, there exists also a lot of software to edit .po files. It is
recommended to use such software, because you will be able to translated much
faster (yes, really).

For now the only tested program is Lokalize, which is part of the KDE software
packages (don't worry, there is a Windows version). Other tools may also work
but please understand that the tools do not support all features of the gettext
file format. With Lokalize, the game can be quickly translated.


5. Create a new .locale file from the original file and the .po file
--------------------------------------------------------------------

This is done with the tool locale2po. Open a command prompt or Linux shell and
cd to the directory where you have the tools available.

An example to convert a Dutch language .po into locale file is:

Linux users:
    mono po2locale.exe -original en.locale -po nl.po -output export.locale -nativename 'NEDERLANDS' -englishname '(DUTCH)'
Windows users:
    po2locale -original en.locale -po nl.po -output export.locale -nativename "NEDERLANDS" -englishname "(DUTCH)"

After executing the command the file export.po has been created. You can copy
this into the games' locale directory and then you can select the new language
in the game.

The po2locale tool supports a few command line options:

  -original      This used to specify the original .locale file that you
                          converted into .po with locale2po.
  -po         This used to specify the .po file that you have edited
  -output      This used to specify the name of the .locale file that
                          needs to be created
  -nativename      This is the name of the language of the new .locale
           file, as it is called in that language itself
  -englishname      This is the name of the language of the new .locale
                          file, as it is called in the English language
  -version      This is the version of the .locale fileformat to use.
                          The current version seems to be 2, and this is
                          the default.


6. Creating a mod
-----------------

Unfortunately, there is no official way to publish your language file into the
workshop, just like you can with assets, maps, colour corrections and styles.
The only solutions to clothe your language file as a mod. However, this
requires programming, increasing the amount of knowledge required to be able
to do it.

In the subdirectory Mod, you will find example files for creating a mod from
your language file. The following instructions assume a Linux system, because
I don't know how to do it on Windows.

The first step is to rename the file, for example if you are translating into
Bulgarian:

mv Mod_Lang_NL.cs Mod_Lang_BG.cs

Next step is to adjust the Makefile

Mod_Lang_NL.dll: Mod_Lang_NL.cs nl.locale
   mcs -target:library -r:ColossalManaged.dll -r:ICities.dll -r:Assembly-CSharp.dll -codepage:utf8 -resource:nl.locale,Mod_Lang_NL.nl.locale $<

... would become:

Mod_Lang_BG.dll: Mod_Lang_BG.cs bg.locale
   mcs -target:library -r:ColossalManaged.dll -r:ICities.dll -r:Assembly-CSharp.dll -codepage:utf8 -resource:bg.locale,Mod_Lang_BG.bg.locale $<

The next step is to adjust the Language codes at the start of the file:

namespace Mod_Lang_NL
{
   public class Mod_Lang_NL : IUserMod
   {
      private string locale_name = "nl";

... would become:

namespace Mod_Lang_BG
{
   public class Mod_Lang_BG : IUserMod
   {
      private string locale_name = "bg";


Now modify the mod names and descriptions at the bottom of the file, i.e.

                default:
                        return "Dutch localization Mod";

... would become:

                default:
                        return "Bulgarian localization Mod";

Copy the files Assembly-CSharp.dll  ColossalManaged.dll  ICities.dll from the
game directory to the mod source code directory.

Type "make", and if everything goes well, you mod will now be created and you
can publish your mod on the Steam Workshop.

The mod source code was originally written by the authors of the Traditional
Chinese translation. Please give their mod a visit and give it a positive vote:

[http://steamcommunity.com/sharedfiles/filedetails/?id=417564312](http://steamcommunity.com/sharedfiles/filedetails/?id=417564312)

I have made some improvements to the source code:
* It only installs the language file if it does not yet already exist, or if
  the file size is not correct
* The activation mechanism is through the OnEnabled method, which is a lot less
  ugly than through the Name method. This also means users can disable the mod
  inside the content manager of the game
* It is multi-lingual itself and will display the mod name and description in
  multiple languages.

```

[COLOR=#101010]This is the Makefile[/COLOR]
```
Mod_Lang_IT.dll: Mod_Lang_IT.cs it.locale
   mcs -target:library -r:ColossalManaged.dll -r:ICities.dll -r:Assembly-CSharp.dll -codepage:utf8 -resource:it.locale,Mod_Lang_IT.it.locale $<

```

[COLOR=#101010]and this is the cs file[/COLOR]

```
using ICities;
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using ColossalFramework.Plugins;
using System.Reflection;

// !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
// !
// ! This mod is based on Chinese Traditional localization https://github.com/ccpz/cities-skylines-Mod_Lang_CHT
// ! Thank you a lot, Taiwanese creators!
// !
// !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

namespace Mod_Lang_IT
{
   public class Mod_Lang_IT : IUserMod
   {
      private string locale_name = "it";

      //
      //the following OS detect code is referring http://stackoverflow.com/questions/10138040/how-to-detect-properly-windows-linux-mac-operating-systems
      //
      public enum Platform
      {
         Windows,
         Linux,
         Mac
      }

      public static Platform RunningPlatform()
      {
         switch (Environment.OSVersion.Platform)
         {
         case PlatformID.Unix:
            // Well, there are chances MacOSX is reported as Unix instead of MacOSX.
            // Instead of platform check, we'll do a feature checks (Mac specific root folders)
            if (Directory.Exists("/Applications")
               & Directory.Exists("/System")
               & Directory.Exists("/Users")
               & Directory.Exists("/Volumes"))
               return Platform.Mac;
            else
               return Platform.Linux;

         case PlatformID.MacOSX:
            return Platform.Mac;

         default:
            return Platform.Windows;
         }
      }

      //------------------------------------------------------------
      // Create destination path to copy the locale file to
      //------------------------------------------------------------
      private string getDestinationPath()
      {
         String dst_path = "";
         #if (DEBUG)
         DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("OS Type: {0}", RunningPlatform().ToString()));
         #endif
         switch (RunningPlatform())
         {
         case Platform.Windows:
            dst_path = "Files\\Locale\\" + locale_name + ".locale";
            break;
         case Platform.Mac:
            dst_path = "Cities.app/Contents/Resources/Files/Locale/" + locale_name + ".locale";
            break;
         case Platform.Linux:
            dst_path = "Files/Locale/" + locale_name + ".locale";
            break;
         }

         #if (DEBUG)
         DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("Destination {0}", dst_path));
         #endif

         return dst_path;
      }

      //------------------------------------------------------------
      // Force to reload the locale manager
      //------------------------------------------------------------
      private void resetLocaleManager(String loc_name)
      {
         // Reload Locale Manager
         ColossalFramework.Globalization.LocaleManager.ForceReload();

         string[] locales = ColossalFramework.Globalization.LocaleManager.instance.supportedLocaleIDs;
         for (int i = 0; i < locales.Length; i++)
         {
            #if (DEBUG)
            DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("Locale index: {0}, ID: {1}", i, locales[i]));
            #endif
            if (locales[i].Equals(loc_name))
            {
               #if (DEBUG)
               DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("Find locale {0} at index: {1}", loc_name, i));
               #endif
               ColossalFramework.Globalization.LocaleManager.instance.LoadLocaleByIndex(i);

               //thanks to: https://github.com/Mesoptier/SkylineToolkit/commit/d33f0bae67662df25bdf8ee2170d95a6999c3721
               ColossalFramework.SavedString lang_setting = new ColossalFramework.SavedString("localeID", "gameSettings");
               #if (DEBUG)
               DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("Current Language Setting: {0}", lang_setting.value));
               #endif
               lang_setting.value = locale_name;
               ColossalFramework.GameSettings.SaveAll();                               
               break;
            }
         }
      }

      //------------------------------------------------------------
      // Locale file size
      //------------------------------------------------------------
      private long LocaleFileSize() {
         Assembly asm = Assembly.GetExecutingAssembly();
         Stream src = asm.GetManifestResourceStream(asm.GetName().Name+"."+locale_name+".locale");
         long l = src.Length;
         src.Close();
         return l;
      }

      //------------------------------------------------------------
      // Copy the locale file
      //------------------------------------------------------------
      private void copyLocaleFile(String dst_path)
      {
         Assembly asm = Assembly.GetExecutingAssembly();
         Stream src = asm.GetManifestResourceStream(asm.GetName().Name+"."+locale_name+".locale");
         #if (DEBUG)
         DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("File size: {0}", st.Length));
         #endif

         FileStream dst = File.Open(dst_path, FileMode.Create);

         byte[] buffer = new byte[8 * 1024];
         int len = 0;
         while ((len = src.Read(buffer, 0, buffer.Length)) > 0)
         {
            dst.Write(buffer, 0, len);
         }
         dst.Close();
         src.Close();
   
         #if (DEBUG)
         DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, String.Format("File write to: {0}", Path.GetFullPath(dst.Name)));
         #endif
      }

      //============================================================
      // Main
      //============================================================
      private void CopyLocaleAndReloadLocaleManager()
      {
         try
         {
            Boolean first_install = true;

            String dst_path = getDestinationPath();

            if ((dst_path.Length > 0) && File.Exists(dst_path))
            {
               FileInfo f = new FileInfo(dst_path);
               if (f.Length == LocaleFileSize())
               {
                  #if (DEBUG)
                  DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, "Locale file is found, user has already used this mod before.");
                  #endif
                  first_install = false;
               }
            }
            if (first_install == true)
            {
               DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, "Locale file for locale "+locale_name+
                  " does not exist or has wrong file size. Installing file to "+dst_path);
               copyLocaleFile(dst_path);
               DebugOutputPanel.AddMessage(PluginManager.MessageType.Message, "Done, game language will now be switched to "+locale_name);
               resetLocaleManager(locale_name);
            }
         }
         catch (Exception e)
         {
//            #if (DEBUG)
            DebugOutputPanel.AddMessage(PluginManager.MessageType.Error, e.ToString());
//            #endif
         }
      }

      //============================================================
      // Modding API
      //============================================================
      public void OnEnabled() {
         CopyLocaleAndReloadLocaleManager ();
      }
      
      public string Name
      {
         get {
            /* We want to make the name of the mod appear in the right language too if the target language is selected. And while
               we are at it, let's add some more languages to be polite to speakers of other language who are trying our mod
               for whatever reason. */
            ColossalFramework.SavedString lang_setting = new ColossalFramework.SavedString("localeID", "gameSettings");
            switch (lang_setting.value) {
               case "de":
                  return "Italienisch Übersetzung Mod";
               case "es":
                  return "Mod Traducción Italiano";
               case "fr":
                  return "Mod Localisation Italienne";
               case "it":
                  return "Mod traduzione Italiana";
               case "nl":
                  return "taliaanse vertaling Mod";
               default:
                  return "Italian localization Mod";
            }
         }
      }

      public string Description
      {
         get {
            /* We want to make the description of the mod appear in the right language too if the target language is selected. And while
               we are at it, let's add some more languages to be polite to speakers of other language who are trying our mod
               for whatever reason. */
            ColossalFramework.SavedString lang_setting = new ColossalFramework.SavedString("localeID", "gameSettings");
            switch (lang_setting.value) {
               case "de":
                  return "Italienische Ubersetzung von Cities: Skylines, durch BopItlia.";
               case "es":
                  return "Traducción italiana de Cities: Skylines, por BopItlia.";
               case "fr":
                  return "Traduction italienne des Cities: Skylines, par BopItlia.";
               case "it":
                  return "Traduzione Italiana Cities: Skyline di BopItlia.";
               case "nl":
                  return "Italiaanse vertaling van Cities: Skylines, door BopItlia.";
               default:
                  return "Italian Localization of Cities:Skylines, by BopItlia.";
            }
         }
      }
   }
}

```

[COLOR=#101010]Other detail I'm using Ubuntu 18.04 downloaded form Microsoft [/COLOR][/FONT][COLOR=#101010][FONT=arial]Store.
[/FONT][/COLOR][FONT=arial][COLOR=#101010]I'm not sure which programm I've installed on it.

Thanks in advance


[/COLOR][/FONT]

---

### Post by TheFu on 2019-10-27
I haven't a clue, but DLLs are Windows.  Linux uses .so and .a files for libraries.  

.so == shared object - a dynamic library, not linked to the program, so later versions can be used, provided the API isn't modified.

.a  == a static library linked to the program.

Any instructions talking about DLLs, are probably for Windows. Search for Linux-specific instructions is my guidance.

---

### Post by staibuz on 2019-10-28
> Search for Linux-specific instructions is my guidance.

I don't understand your answer.


The instructions I posted clearly state that you have to use linux to create the dll file.

The author of the guide, indeed, say clearly :**```
*The following instructions assume a Linux system, because ******I don't know how to do it on Windows.
```***
I have followed this instruction point to point but I can't reach the final result (= a dll file).

So I ask again help to understand why when I execute the makefile I receive the cs0009 error. 

[FONT=arial]I receive[/FONT]

---

### Post by Holger_Gehrke on 2019-10-28
The message isn't generated by make, it's the c#-compiler (mcs) complaining that something is wrong with your dll-files (mono uses dll-files both on Windows and on Linux for libraries that contain non-native code). It's expecting the dll-files to contain metadata in some specific form and not finding it.

And by the way, you're not really using Ubuntu, you're using an Ubuntu userland on top of the Windows-Subsystem for Linux (that's basically Windows attempting to translate Linux system calls into Windows system calls), which creates it's own set compatibility problems ...

You might be better of asking your questions in the forum where you found the instructions you're quoting, the probability of anybody here being familiar enough with mono and with the game you're trying to translate are not really good ...

Holger

---

### Post by staibuz on 2019-10-29
I try to contact the author but he seems no longer active

---

### Post by staibuz on 2019-11-04
No other dares to answer?

---

### Post by staibuz on 2019-12-08
Someone could help me?

---

### Post by spjackson on 2019-12-08
You need a programmer with expertise in mono and mcs and possibly Steam. While it may be possible that someone here can help you,  I'm not sure that "New to Ubuntu" is the best forum in which to find such expertise. Personally speaking, I have been programming on Unix/Linux and Windows for over 30 years but I have never used these tools, which is why I cannot help.

---

