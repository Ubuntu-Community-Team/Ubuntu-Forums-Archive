---
title: "MonoDevelop - ASP.NET Problem"
date: 2010-03-11
forum: Programming Talk
---

### Post by issachan on 2010-03-11
Hi everybody,

I need help! I'm trying to upload a website I created in MonoDevelop onto my server but I keep getting the following error: 

> **Server Error in '/clients/survey2010/preventure' Application.**

              ** *Configuration Error* **

              [FONT=Arial, Helvetica, Geneva, SunSans-Regular, sans-serif]              ** Description: **An error occurred during the processing of a configuration file required to service this request. Please review the specific error details below and modify your configuration file appropriately. 

             ** Parser Error Message: **Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies. The system cannot find the file specified.

             **Source Error:** 

                                                                       Line 11:     <compilation defaultLanguage="C#" debug="true">
Line 12:       <assemblies>
[COLOR=red]Line 13:         <add assembly="gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f" />
[/COLOR]Line 14:       </assemblies>
Line 15:     </compilation>                                                               
             ** Source File: ** D:\Hosting\5509999\html\clients\survey2010\preventure\web.config**    Line: ** 13             

             **Assembly Load Trace:** The following information can be helpful to determine why the assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' could not be loaded.

                                                                       WRN: Assembly binding logging is turned OFF.
To enable assembly bind failure logging, set the registry value [HKLM\Software\Microsoft\Fusion!EnableLog] (DWORD) to 1.
Note: There is some performance penalty associated with assembly bind failure logging.
To turn this feature off, remove the registry value [HKLM\Software\Microsoft\Fusion!EnableLog].
                                                              
                           **Version Information:** Microsoft .NET Framework Version:2.0.50727.3603; ASP.NET Version:2.0.50727.4049              [/FONT][SIZE=2]What does it mean and how do I fix it?[/SIZE]
Here's the page in question... [http://www.mythandmagicstudios.com/clients/survey2010/preventure/default.aspx](http://www.mythandmagicstudios.com/clients/survey2010/preventure/default.aspx)

---

### Post by crush304 on 2010-03-11
how/why are you using gtk libraries in your website.

I would think you should delete the entire line 13 and then see what breaks

---

### Post by crush304 on 2010-03-11
if you really need that assembly reference you'll need to find the dll for gtk-sharp and put it in your /bin folder

---

### Post by issachan on 2010-03-11
Oooh.. that makes sense. Sorry I'm new to a lot of things these days.. I'm just learning asp.net so forgive me for asking dumb questions and the like.. 

I don't know what gtk-sharp is doing there, I just assumed it had to be there because it was there when I started a new project. I'm more familiar with PHP, I'm only learning asp.net because I'm forced to learn it in class. 

Thank you!

---

