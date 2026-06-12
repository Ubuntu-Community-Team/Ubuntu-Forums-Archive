---
title: "Wine   v0.9.55  Missing dependency"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by David1000 on 2008-05-11
I read that wine for 8.04 is completely broken; which may be why I couldn't get it to work.  I also read that wine v0.9.55 for Gutsy did work on 8.04 Hardy.  So I downloaded a debian file, .deb v0.9.55 for Gutsy and tried to install.  Got the error message:

Error:  Dependency is not satisfiable : libldap2.

So I downloaded this file and installed using the package manager.  No luck - still get the same error message.
Same thing with v0.9.47 for Gutsy.

Ideas?

---

### Post by macaholic on 2008-05-11
Try using the wine repository, [http://winehq.org/site/download-deb/](http://winehq.org/site/download-deb/) Btw, the latest version of wine is 1.0 rc1.

---

### Post by David1000 on 2008-05-11
Tried that.  Was probably a repeat of what I had done earlier.  Latest Wine doesn't work with Hardy 8.04 according to what is on this forum.

More details of my problem with the latest version of wine (as opposed to a problem with the old version as above;:


I have installed wine with no apparent problems.  The configuration file opens OK via either winecfg or applications/wine/configure wine.  

I can open notes by applications/wine/programs/accessories/notepad.  If I open winefile using the terminal, I get the following message in the terminal:

david@AMD5200:~$ wine winefile
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 6/04/2008, dlt (d/m/y): 28/09/2008

And winefile opens.  

I can navigate to the CD ROM and get a listing of files on the CD.  If I then click on, say an ini file on the CD, I get the message:

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

And the ini file is displayed in notepad.

If I click on say the Quicken 7.5 installation executable file, I get the message:

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing

And nothing happens.

In the terminal, I can go to the CD by cd /media/cdrom0.  ls -l gives a correct file listing.  But wine dir gives error message as follows:
david@AMD5200:/media/cdrom0$ wine dir
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"c:\\windows\\system32\\dir.exe": Module not found
david@AMD5200:/media/cdrom0$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))


So, there appears to be a problem.

---

