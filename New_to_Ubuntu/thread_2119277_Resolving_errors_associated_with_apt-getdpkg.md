---
title: "Resolving errors associated with apt-get/dpkg"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by Scrumps on 2013-02-23
First off, I tried this: 
[http://ubuntuforums.org/showpost.php?p=5962046&postcount=9](http://ubuntuforums.org/showpost.php?p=5962046&postcount=9)

Which doesn't work for me.

Anyways, I was removing files for a program that I thought was removed, but was actually still installed. I was trying to start over from scratch, and I noticed that purge wasn't always removing the folders. I found this out too late, and now I can't do anything with apt-get or dpkg because it throws an error every single time.

This is a pastebin of ALL the commands that I have done in trying to resolve this. However, the problem is occuring because I removed stuff from "/var/lib/postgresql", "/run/postgresql", "/etc/postgresql".

```

andrew@server:~/Downloads$ sudo apt-get purge postgresql-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'postgresql' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
andrew@server:~/Downloads$ sudo apt-get purge postgresql-9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libossp-uuid16
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  postgresql-9.1* postgresql-contrib* postgresql-contrib-9.1*
0 upgraded, 0 newly installed, 3 to remove and 9 not upgraded.
After this operation, 13.8 MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 202290 files and directories currently installed.)
Removing postgresql-contrib ...
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--purge):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing postgresql-9.1 ...
/var/lib/dpkg/info/postgresql-9.1.prerm: 9: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.1 (--purge):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 postgresql-contrib-9.1
 postgresql-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo apt-get purge postgresql-9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libossp-uuid16
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  postgresql-9.1* postgresql-contrib-9.1*
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
2 not fully installed or removed.
After this operation, 13.7 MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 202287 files and directories currently installed.)
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--purge):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing postgresql-9.1 ...
/var/lib/dpkg/info/postgresql-9.1.prerm: 9: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.1 (--purge):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 postgresql-contrib-9.1
 postgresql-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo apt-get --help
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
andrew@server:~/Downloads$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del boot-repair 3.197~ppa29~quantal [47.5 kB]
Del google-chrome-unstable 26.0.1410.3-r181934 [39.3 MB]
Del clean-ubiquity 3.197~ppa30~quantal [6,806 B]
Del boot-sav-extra 3.197~ppa31~quantal [142 kB]
Del os-uninstaller 3.197~ppa31~quantal [11.7 kB]
Del tesseract-ocr-eng 3.02.02+svn822-1ppa1~quantal1 [6,795 kB]
Del clean-ubiquity 3.197~ppa28~quantal [6,772 B]
Del os-uninstaller 3.197~ppa29~quantal [11.7 kB]
Del os-uninstaller 3.197~ppa30~quantal [11.7 kB]
Del openjdk-7-jre-headless 7u13-2.3.6-0ubuntu0.12.10.1 [35.4 MB]
Del flashplugin-installer 11.2.202.262ubuntu0.12.10.1 [7,410 B]
Del openjdk-6-jre-lib 6b27-1.12.1-2ubuntu0.12.10.2 [6,139 kB]
Del boot-repair 3.197~ppa28~quantal [46.9 kB]
Del libgimp2.0 2.8.2+git20130125-1ppa1~quantal1 [1,252 kB]
Del clementine 1.1.0+git20130123-1ppa1~quantal1 [4,032 kB]
Del clean-ubiquity 3.197~ppa29~quantal [6,810 B]
Del gimp 2.8.2+git20130125-1ppa1~quantal1 [5,330 kB]
Del linux-libc-dev 3.5.0-23.35 [894 kB]
Del clean-ubiquity 3.197~ppa31~quantal [6,776 B]
Del boot-sav 3.197~ppa29~quantal [386 kB]
Del boot-sav-extra 3.197~ppa29~quantal [142 kB]
Del google-chrome-unstable 26.0.1397.2-r179372 [39.1 MB]
Del boot-repair 3.197~ppa30~quantal [46.9 kB]
Del boot-sav 3.197~ppa30~quantal [382 kB]
Del openjdk-7-jre-lib 7u13-2.3.6-0ubuntu0.12.10.1 [5,538 kB]
Del openjdk-7-jre 7u13-2.3.6-0ubuntu0.12.10.1 [227 kB]
Del boot-repair 3.197~ppa31~quantal [46.9 kB]
Del libgegl-0.2-0 0.2.0+git20130120-1ppa1~quantal1 [658 kB]
Del linux-libc-dev 3.5.0-23.35 [897 kB]
Del boot-sav-extra 3.197~ppa30~quantal [142 kB]
Del google-chrome-unstable 26.0.1410.5-r182376 [39.1 MB]
Del firefox-locale-en 18.0.2+build1-0ubuntu0.12.10.1 [490 kB]
Del tesseract-ocr 3.02.02+svn822-1ppa1~quantal1 [74.0 kB]
Del icedtea-7-jre-jamvm 7u13-2.3.6-0ubuntu0.12.10.1 [587 kB]
Del os-uninstaller 3.197~ppa28~quantal [11.7 kB]
Del libtesseract3 3.02.02+svn822-1ppa1~quantal1 [1,098 kB]
Del google-chrome-unstable 26.0.1403.0-r180337 [39.2 MB]
Del google-chrome-unstable 26.0.1410.10-r183151 [39.3 MB]
Del boot-sav 3.197~ppa31~quantal [380 kB]
Del firefox-globalmenu 18.0.2+build1-0ubuntu0.12.10.1 [50.0 kB]
Del boot-sav-extra 3.197~ppa28~quantal [142 kB]
Del boot-sav 3.197~ppa28~quantal [379 kB]
Del gimp-data 2.8.2+git20130125-1ppa1~quantal1 [13.8 MB]
Del firefox 18.0.2+build1-0ubuntu0.12.10.1 [23.8 MB]
andrew@server:~/Downloads$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libossp-uuid16 postgresql-contrib-9.1
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
2 not fully installed or removed.
After this operation, 2,168 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 202287 files and directories currently installed.)
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
/var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing libossp-uuid16 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 postgresql-contrib-9.1 : Depends: libossp-uuid16 but it is not installed
E: Unmet dependencies. Try using -f.
andrew@server:~/Downloads$ sudo apt-get --help
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
andrew@server:~/Downloads$ sudo apt-get -f
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
andrew@server:~/Downloads$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  postgresql-contrib-9.1
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
2 not fully installed or removed.
After this operation, 2,031 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 202280 files and directories currently installed.)
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo apt-get install postgresql-contrib
postgresql-contrib      postgresql-contrib-9.1  
andrew@server:~/Downloads$ sudo apt-get install postgresql-contrib-9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-contrib-9.1 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 postgresql-contrib-9.1 : Depends: libossp-uuid16 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
andrew@server:~/Downloads$ sudo apt-get -f install postgresql-contrib-9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-contrib-9.1 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 postgresql-contrib-9.1 : Depends: libossp-uuid16 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
andrew@server:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libossp-uuid16 postgresql-contrib-9.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libossp-uuid16
Suggested packages:
  uuid
The following NEW packages will be installed:
  libossp-uuid16
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0 B/51.6 kB of archives.
After this operation, 137 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously unselected package libossp-uuid16.
(Reading database ... 202286 files and directories currently installed.)
Unpacking libossp-uuid16 (from .../libossp-uuid16_1.6.2-1.3_amd64.deb) ...
Setting up postgresql-9.1 (9.1.8-0ubuntu12.10) ...
/var/lib/dpkg/info/postgresql-9.1.postinst: 9: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libossp-uuid16 (1.6.2-1.3) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.8-0ubuntu12.10); however:
  Package postgresql-9.1 is not configured yet.

dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-9.1
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo apt-get --help
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
andrew@server:~/Downloads$ 
andrew@server:~/Downloads$ 
andrew@server:~/Downloads$ sudo dpkg --help
Usage: dpkg [<option> ...] <command>

Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  --triggers-only    <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --add-architecture <arch>        Add <arch> to the list of architectures.
  --remove-architecture <arch>     Remove <arch> from the list of architectures.
  --print-architecture             Print dpkg architecture.
  --print-foreign-architectures    Print allowed foreign architectures.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.

  -?, --help                       Show this help message.
      --version                    Show the version.

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep |
  --assert-multi-arch.

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  --path-exclude=<pattern>   Do not install paths which match a shell pattern.
  --path-include=<pattern>   Re-include a pattern after a previous exclusion.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --[no-]triggers            Skip or force consequential trigger processing.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --status-logger=<command>  Send status change updates to <command>'s stdin.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.

Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.
andrew@server:~/Downloads$ sudo dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 postgresql-9.1       object-relational SQL database, version 9.1 server
 postgresql-contrib-9.1 additional facilities for PostgreSQL

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 dhcping              DHCP Daemon Ping Program

andrew@server:~/Downloads$ sudo dpkg --configure postgresql-9.1
Setting up postgresql-9.1 (9.1.8-0ubuntu12.10) ...
/var/lib/dpkg/info/postgresql-9.1.postinst: 9: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 postgresql-9.1
andrew@server:~/Downloads$ sudo dpkg --force-help
dpkg forcing options - control behaviour when problems found:
  warn but continue:  --force-<thing>,<thing>,...
  stop with error:    --refuse-<thing>,<thing>,... | --no-force-<thing>,...
 Forcing things:
  [!] all                Set all force options
  [*] downgrade          Replace a package with a lower version
      configure-any      Configure any package which may help this one
      hold               Process incidental packages even when on hold
      not-root           Try to (de)install things even when not root
      bad-path           PATH is missing important programs, problems likely
      bad-verify         Install a package even if it fails authenticity check
      bad-version        Process even packages with wrong versions
      overwrite          Overwrite a file from one package with another
      overwrite-diverted Overwrite a diverted file with an undiverted version
  [!] overwrite-dir      Overwrite one package's directory with another's file
  [!] unsafe-io          Do not perform safe I/O operations when unpacking
  [!] confnew            Always use the new config files, don't prompt
  [!] confold            Always use the old config files, don't prompt
  [!] confdef            Use the default option for new config files if one
                         is available, don't prompt. If no default can be found,
                         you will be prompted unless one of the confold or
                         confnew options is also given
  [!] confmiss           Always install missing config files
  [!] confask            Offer to replace config files with no new versions
  [!] architecture       Process even packages with wrong or no architecture
  [!] breaks             Install even if it would break another package
  [!] conflicts          Allow installation of conflicting packages
  [!] depends            Turn all dependency problems into warnings
  [!] depends-version    Turn dependency version problems into warnings
  [!] remove-reinstreq   Remove packages which require installation
  [!] remove-essential   Remove an essential package

WARNING - use of options marked [!] can seriously damage your installation.
Forcing options marked [*] are enabled by default.
andrew@server:~/Downloads$ sudo dpkg --force-! postgresql
dpkg: error: unknown force/refuse option `!'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --force-all postgresql
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --force-all
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --force-all^C
andrew@server:~/Downloads$ sudo apt-get --hep
E: Command line option --hep is not understood
andrew@server:~/Downloads$ sudo apt-get --help
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
andrew@server:~/Downloads$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libossp-uuid16 postgresql-contrib-9.1
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
2 not fully installed or removed.
After this operation, 2,168 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 202287 files and directories currently installed.)
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing libossp-uuid16 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo apt-get build-dep
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Must specify at least one package to check builddeps for
andrew@server:~/Downloads$ sudo apt-get build-dep postgresql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'postgresql-common' as source package instead of 'postgresql'
The following packages will be REMOVED:
  postgresql-contrib-9.1
The following NEW packages will be installed:
  debhelper dh-apparmor html2text po-debconf
0 upgraded, 4 newly installed, 1 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 936 kB of archives.
After this operation, 228 kB disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main html2text amd64 1.3.2a-15build1 [93.3 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main po-debconf all 1.0.16+nmu2ubuntu1 [210 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main dh-apparmor all 2.8.0-0ubuntu5 [9,846 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main debhelper all 9.20120608ubuntu1 [623 kB]
Fetched 936 kB in 1s (756 kB/s)
(Reading database ... 202280 files and directories currently installed.)
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
/var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
andrew@server:~/Downloads$ sudo apt-get purge postgresql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'postgresql' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 postgresql-contrib-9.1 : Depends: libossp-uuid16 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
andrew@server:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libossp-uuid16 postgresql-contrib-9.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libossp-uuid16
Suggested packages:
  uuid
The following NEW packages will be installed:
  libossp-uuid16
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0 B/51.6 kB of archives.
After this operation, 137 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously unselected package libossp-uuid16.
(Reading database ... 202286 files and directories currently installed.)
Unpacking libossp-uuid16 (from .../libossp-uuid16_1.6.2-1.3_amd64.deb) ...
Setting up postgresql-9.1 (9.1.8-0ubuntu12.10) ...
/var/lib/dpkg/info/postgresql-9.1.postinst: 9: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libossp-uuid16 (1.6.2-1.3) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.8-0ubuntu12.10); however:
  Package postgresql-9.1 is not configured yet.

dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-9.1
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ find / -iname "postgre*" -type d
/srv/storage/Firefox-sync-server/server-full/lib/python2.7/site-packages/sqlalchemy/dialects/postgresql
find: `/srv/games/.Trash-1002': Permission denied
^C
andrew@server:~/Downloads$ sudo find / -iname "postgre*" -type d
/srv/storage/Firefox-sync-server/server-full/lib/python2.7/site-packages/sqlalchemy/dialects/postgresql
/usr/share/webmin/gray-theme/postgresql
/usr/share/webmin/blue-theme/postgresql
/usr/share/webmin/mscstyle3/postgresql
/usr/share/webmin/postgresql
/usr/share/webmin/caldera/postgresql
/etc/webmin/postgresql
andrew@server:~/Downloads$ sudo find / -iname "postgre*" -type f
/srv/storage/Firefox-sync-server/server-full/lib/python2.7/site-packages/sqlalchemy/dialects/postgres.pyc
/srv/storage/Firefox-sync-server/server-full/lib/python2.7/site-packages/sqlalchemy/dialects/postgres.py
/var/lib/update-rc.d/postgresql
/var/lib/dpkg/info/postgresql-common.postinst
/var/lib/dpkg/info/postgresql-common.list
/var/lib/dpkg/info/postgresql-client-common.list
/var/lib/dpkg/info/postgresql-common.triggers
/var/lib/dpkg/info/postgresql-client-9.1.postinst
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm
/var/lib/dpkg/info/postgresql-common.prerm
/var/lib/dpkg/info/postgresql-common.config
/var/lib/dpkg/info/postgresql-9.1.list
/var/lib/dpkg/info/postgresql-contrib-9.1.md5sums
/var/lib/dpkg/info/postgresql-9.1.md5sums
/var/lib/dpkg/info/postgresql-common.templates
/var/lib/dpkg/info/postgresql-common.postrm
/var/lib/dpkg/info/postgresql-contrib-9.1.list
/var/lib/dpkg/info/postgresql-contrib-9.1.postinst
/var/lib/dpkg/info/postgresql-9.1.preinst
/var/lib/dpkg/info/postgresql-common.conffiles
/var/lib/dpkg/info/postgresql-client-common.md5sums
/var/lib/dpkg/info/postgresql-common.md5sums
/var/lib/dpkg/info/postgresql-9.1.prerm
/var/lib/dpkg/info/postgresql-client-9.1.list
/var/lib/dpkg/info/postgresql-client-9.1.prerm
/var/lib/dpkg/info/postgresql-client-9.1.md5sums
/var/lib/dpkg/info/postgresql-9.1.postrm
/var/lib/dpkg/info/postgresql-9.1.postinst
/var/lib/dpkg/info/postgresql-common.preinst
/var/lib/dpkg/info/postgresql-client-common.conffiles
/var/lib/dpkg/info/postgresql-client-common.postrm
/var/crash/postgresql-contrib-9.1.0.crash
/var/cache/apt/archives/postgresql-client-common_136_all.deb
/var/cache/apt/archives/postgresql-client-9.1_9.1.8-0ubuntu12.10_amd64.deb
/var/cache/apt/archives/postgresql-contrib_9.1+136_all.deb
/var/cache/apt/archives/postgresql_9.1+136_all.deb
/var/cache/apt/archives/postgresql-contrib-9.1_9.1.8-0ubuntu12.10_amd64.deb
/var/cache/apt/archives/postgresql-common_136_all.deb
/var/cache/apt/archives/postgresql-9.1_9.1.8-0ubuntu12.10_amd64.deb
/usr/share/lintian/overrides/postgresql-common
/usr/share/lintian/overrides/postgresql-client-common
/usr/share/man/man5/postgresqlrc.5.gz
/usr/share/webmin/status/postgresql-monitor.pl
/usr/share/webmin/status/services/postgresql.serv
/usr/share/webmin/postgresql/postgresql-lib.pl
/etc/init.d/postgresql
/etc/logrotate.d/postgresql-common
/etc/webmin/status/services/postgresql.serv
andrew@server:~/Downloads$ 
andrew@server:~/Downloads$ 
andrew@server:~/Downloads$ sudo dpkg --purge
dpkg: error: --purge needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --purge postgresql-c
postgresql-client-9.1     postgresql-client-common  postgresql-common         
andrew@server:~/Downloads$ sudo dpkg --purge postgresql-c
postgresql-client-9.1     postgresql-client-common  postgresql-common         
andrew@server:~/Downloads$ sudo dpkg --purge postgresql-client-
postgresql-client-9.1     postgresql-client-common  
andrew@server:~/Downloads$ sudo dpkg --purge postgresql-client-9.1 
(Reading database ... 202287 files and directories currently installed.)
Removing postgresql-client-9.1 ...
/var/lib/dpkg/info/postgresql-client-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-client-9.1 (--purge):
 subprocess installed pre-removal script returned error exit status 2
/var/lib/dpkg/info/postgresql-client-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 postgresql-client-9.1
andrew@server:~/Downloads$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                                                                                                                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                                                                                                                
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]                                                                                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                                                                                                                                                                               
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                                                                                                                                                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]                                                                                                                                            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                                                                                                                                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                                                                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                                                                                                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg [933 B]                                                                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                      
Hit [http://deb.torproject.org](http://deb.torproject.org) quantal InRelease                                                                                                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg [933 B]                                                                                         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [32.6 kB]                                                                                         
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                                                                                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                                                                                                                                          
Hit [http://deb.torproject.org](http://deb.torproject.org) quantal/main amd64 Packages                                                                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                                                
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release [49.6 kB]                                                                                          
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]                                                                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                                                                                                                                 
Hit [http://deb.torproject.org](http://deb.torproject.org) quantal/main i386 Packages                                                                                                                
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [15.4 kB]                                                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                                                                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                                                                         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release [49.6 kB]                                                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                                                                                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                                                                             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [701 B]                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                                                           
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [88.5 kB]                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                             
Ign [http://deb.torproject.org](http://deb.torproject.org) quantal/main Translation-en_US                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages                                                            
Ign [http://deb.torproject.org](http://deb.torproject.org) quantal/main Translation-en                                                                                 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                                                     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [41.6 kB]                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,146 B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                                                        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [88.0 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                    
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]                                  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [42.1 kB]                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                           
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources [79.7 kB]                                                    
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,400 B]                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                                                                   
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]            
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources [78.9 kB]                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                                                           
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources [2,941 B]                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                          
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages [205 kB]             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                  
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [3,048 B]                              
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages [168 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                                                      
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,948 B]       
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages [204 kB]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                         
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]        
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages [169 kB]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US                  
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,098 B]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources [14 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources [14 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources [7,732 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources [781 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                       
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages [14 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages [11.3 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages [1,118 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                 
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages [12.1 kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages [1,118 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US                                                                                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US                                                                                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US                                                                                                                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US                                                                                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US                                                                                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US                                                                                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US                                                                                                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US                                                                                                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US                                                                                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US                                                                                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US                                                                                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                                                                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                                                                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                                                                                                                                                                 s
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                                                                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                                                                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                                                                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                                                                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                                                                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                                                                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                                                                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                                                                                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                                                                                                                                                                                    
Fetched 1,429 kB in 11s (120 kB/s)                                                                                                                                                                                                          
Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
You may want to run apt-get update to correct these problems
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
andrew@server:~/Downloads$ ssudo apt-get update
No command 'ssudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
ssudo: command not found
andrew@server:~/Downloads$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                                                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                                                                                                                                                                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                                                                                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                                                                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                                                                                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                           
Hit [http://deb.torproject.org](http://deb.torproject.org) quantal InRelease                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                                                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                                                                                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                                                                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                                                                                                    
Hit [http://deb.torproject.org](http://deb.torproject.org) quantal/main amd64 Packages                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                                                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                                                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources                                                                           
Hit [http://deb.torproject.org](http://deb.torproject.org) quantal/main i386 Packages                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                                                                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                                                                                
Ign [http://deb.torproject.org](http://deb.torproject.org) quantal/main Translation-en_US                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages                  
Ign [http://deb.torproject.org](http://deb.torproject.org) quantal/main Translation-en                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
andrew@server:~/Downloads$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
andrew@server:~/Downloads$ sudo apt-get clean
andrew@server:~/Downloads$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libossp-uuid16 postgresql-contrib-9.1
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
3 not fully installed or removed.
After this operation, 2,168 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 202287 files and directories currently installed.)
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
/var/lib/dpkg/info/postgresql-contrib-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing libossp-uuid16 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-contrib-9.1
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ sudo dpkg --remove -force --force-remov-reinstreq postgresql-contrib-9.1
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --remove -force --force-remove-reinstreq postgresql-contrib-9.1
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --remove -force --force-remove-reinstreq postgresql-common
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$

``` 

The bottom of that list accurately reflects the steps in Gazneth's steps, but I severely screwed this up, and I can't figure out how to fix it.

If I try to resolve it by following the onscreen directions of running "sudo apt-get -f install libossp-uuid16":
```

andrew@server:~/Downloads$ sudo apt-get -f install libossp-uuid16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  postgresql-contrib-9.1
Use 'apt-get autoremove' to remove it.
Suggested packages:
  uuid
The following NEW packages will be installed:
  libossp-uuid16
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
3 not fully installed or removed.
Need to get 51.6 kB of archives.
After this operation, 137 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/main libossp-uuid16 amd64 1.6.2-1.3 [51.6 kB]
Fetched 51.6 kB in 0s (224 kB/s)          
Selecting previously unselected package libossp-uuid16.
(Reading database ... 202286 files and directories currently installed.)
Unpacking libossp-uuid16 (from .../libossp-uuid16_1.6.2-1.3_amd64.deb) ...
Setting up postgresql-client-9.1 (9.1.8-0ubuntu12.10) ...
/var/lib/dpkg/info/postgresql-client-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-client-9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of postgresql-9.1:
 postgresql-9.1 depends on postgresql-client-9.1; however:
  Package postgresql-client-9.1 is not configured yet.

dpkg: error processing postgresql-9.1 (--configure):
 dependency problems - leaving unconfigured
Setting up libossp-uuid16 (1.6.2-1.3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.8-0ubuntu12.10); however:
  Package postgresql-9.1 is not configured yet.

dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-client-9.1
 postgresql-9.1
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@server:~/Downloads$ 

```

---

### Post by matt_symes on 2013-02-23
Hi

This did not work for you ?

```
sudo dpkg --remove -force --force-remove-reinstreq postgrel*
```You can download the package and try to reinstall it using dpkg.

Failing that you can edit the file

```
/var/lib/dpkg/status
```and remove all references to postgrel.

Kind regards

---

### Post by Scrumps on 2013-02-23
Hey matt, thanks for quick reply.

Unfortunately, no, it didn't. 
> 
andrew@server:~/Downloads$ sudo dpkg --remove -force --force-remove-reinstreq postgrel*
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


As far as downloading the package, with out it installing, how would I do that?

This commands? :
sudo apt-get download packagenamehere


For the last thing you mentioned? Would I have to remove the entire thing like so...
> 
Package: libpq5
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 640
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: postgresql-9.1
Version: 9.1.8-0ubuntu12.10
Depends: libc6 (>= 2.14), libcomerr2 (>= 1.01), libgssapi-krb5-2 (>= 1.10+dfsg~), libkrb5-3 (>= 1.6.dfsg.2), libldap-2.4-2 (>= 2.4.7), libssl1.0.0 (>= 1.0.0)
Description: PostgreSQL C client library
 libpq is a C library that enables user programs to communicate with
 the PostgreSQL database server.  The server can be on another machine
 and accessed through TCP/IP.  This version of libpq is compatible
 with servers from PostgreSQL 8.2 or later.
 .
 This package contains the run-time library, needed by packages using
 libpq.
 .
 PostgreSQL is an object-relational SQL database management system.
Homepage: [http://www.postgresql.org/](http://www.postgresql.org/)
Original-Maintainer: Debian PostgreSQL Maintainers <pkg-postgresql-public@lists.alioth.debian.org>

Package: postgresql-contrib-9.1
Status: deinstall ok half-configured
Priority: optional
Section: database
Installed-Size: 1983
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: postgresql-9.1
Version: 9.1.8-0ubuntu12.10
Config-Version: 9.1.8-0ubuntu12.10
Depends: postgresql-9.1 (= 9.1.8-0ubuntu12.10), libc6 (>= 2.15), libossp-uuid16, libpq5 (>= 9.0~), libssl1.0.0 (>= 1.0.0), libxml2 (>= 2.7.4), libxslt1.1 (>= 1.1.25), zlib1g (>= 1:1.1.4), postgresql-common (>= 115~)
Suggests: libdbd-pg-perl
Conflicts: postgresql-contrib (<< 7.5)
Description: additional facilities for PostgreSQL
 The PostgreSQL contrib package provides several additional features
 for the PostgreSQL database. This version is built to work with the
 server package postgresql-9.1.  contrib often serves as a testbed for
 features before they are adopted into PostgreSQL proper:
 .
  adminpack      - File and log manipulation routines, used by pgAdmin
  btree_gist     - B-Tree indexing using GiST (Generalised Search Tree)
  chkpass        - An auto-encrypted password datatype
  cube           - Multidimensional-cube datatype (GiST indexing example)
  dblink         - Functions to return results from a remote database
  earthdistance  - Operator for computing the distance (in miles) between
                   two points on the earth's surface
  fuzzystrmatch  - Levenshtein, metaphone, and soundex fuzzy string matching
  hstore         - Store (key, value) pairs
  intagg         - Integer aggregator/enumerator
  _int           - Index support for arrays of int4, using GiST (benchmark
                   needs the libdbd-pg-perl package)
  isn            - type extensions for ISBN, ISSN, ISMN, EAN13 product numbers
  lo             - Large Object maintenance
  ltree          - Tree-like data structures
  oid2name       - Maps OIDs to table names
  pageinspect    - Inspection of database pages
  passwordcheck  - Simple password strength checker
  pg_buffercache - Real time queries on the shared buffer cache
  pg_freespacemap- Displays the contents of the free space map (FSM)
  pg_trgm        - Determine the similarity of text based on trigram matching
  pg_standby     - Create a warm stand-by server
  pgbench        - TPC-B like benchmark
  pgcrypto       - Cryptographic functions
  pgrowlocks     - A function to return row locking information
  pgstattuple    - Returns the percentage of dead tuples in a table; this
                   indicates whether a vacuum is required.
  seg            - Confidence-interval datatype (GiST indexing example)
  spi            - PostgreSQL Server Programming Interface; 4 examples of
                   its use:
                   autoinc    - A function for implementing AUTOINCREMENT/
                                IDENTITY
                   insert_username - function for inserting user names
                   moddatetime - Update modification timestamps
                   refint     - Functions for implementing referential
                                integrity (foreign keys).  Note that this is
                                now superseded by built-in referential
                                integrity.
                   timetravel - Re-implements in user code the time travel
                                feature that was removed in 6.3.
  tablefunc      - examples of functions returning tables
  uuid-ossp      - UUID generation functions
  vacuumlo       - Remove orphaned large objects
 .
 PostgreSQL is an object-relational SQL database management system.
Homepage: [http://www.postgresql.org/](http://www.postgresql.org/)
Original-Maintainer: Debian PostgreSQL Maintainers <pkg-postgresql-public@lists.alioth.debian.org>


Like I mentioned, thanks. I have been getting frustrated with this going no where from my own end.

---

### Post by matt_symes on 2013-02-23
Hi

Try this command

```
sudo dpkg --remove --force-remove-reinstreq postgrel*
```If that does not work then you need to edit the status file. Make a backup first.

```
sudo cp /var/lib/dpkg/status{,.bk}
```Remove all references to the problem packages. Packages a delimited by blank lines. In your previous post, that is what you need to remove.

Kind regards

---

### Post by Scrumps on 2013-02-23
```
andrew@server:~/Downloads$ sudo aptitude reinstall postgresql-\*
Couldn't find any package whose name or description matched "postgresql-*"
Couldn't find any package whose name or description matched "postgresql-*"
The following partially installed packages will be configured:
  postgresql-9.1 postgresql-client-9.1 postgresql-contrib-9.1 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up postgresql-client-9.1 (9.1.8-0ubuntu12.10) ...
/var/lib/dpkg/info/postgresql-client-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-client-9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of postgresql-9.1:
 postgresql-9.1 depends on postgresql-client-9.1; however:
  Package postgresql-client-9.1 is not configured yet.

dpkg: error processing postgresql-9.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.8-0ubuntu12.10); however:
  Package postgresql-9.1 is not configured yet.

dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                          Errors were encountered while processing:
 postgresql-client-9.1
 postgresql-9.1
 postgresql-contrib-9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
                                         
andrew@server:~/Downloads$ sudo aptitude reinstall postgresql-client-9.1 postgresql-9.1 postgresql-contrib-9.1
The following packages will be REINSTALLED:
  postgresql-9.1 postgresql-client-9.1 postgresql-contrib-9.1 
0 packages upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Internal Error, No file name for postgresql-client-9.1:amd64
                                         
andrew@server:~/Downloads$ sudo aptitude reinstall postgresql-9.1 postgresql-contrib-9.1
The following packages will be REINSTALLED:
  postgresql-9.1 postgresql-contrib-9.1 
The following partially installed packages will be configured:
  postgresql-client-9.1 
0 packages upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Internal Error, No file name for postgresql-9.1:amd64
                                         
andrew@server:~/Downloads$ sudo aptitude reinstall postgresql-contrib-9.1
The following packages will be REINSTALLED:
  postgresql-contrib-9.1 
The following partially installed packages will be configured:
  postgresql-9.1 postgresql-client-9.1 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Internal Error, No file name for postgresql-contrib-9.1:amd64
                                         
andrew@server:~/Downloads$ sudo postgresql-client-9.1 postgresql-9.1 postgresql-contrib-9.1^C
andrew@server:~/Downloads$ sudo dpkg --remove --force-remove-reinstreq postgrel*
dpkg: error: --remove needs a valid package name but 'postgrel*' is not: illegal package name in specifier 'postgrel*': character `*' not allowed (only letters, digits and characters `-+._')

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andrew@server:~/Downloads$ sudo dpkg --remove --force-remove-reinstreq postgresql-client-9.1 postgresql-9.1 postgresql-contrib-9.1
(Reading database ... 202433 files and directories currently installed.)
Removing postgresql-client-9.1 ...
/var/lib/dpkg/info/postgresql-client-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-client-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
/var/lib/dpkg/info/postgresql-client-9.1.postinst: 7: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing postgresql-9.1 ...
/var/lib/dpkg/info/postgresql-9.1.prerm: 9: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
Removing postgresql-contrib-9.1 ...
/var/lib/dpkg/info/postgresql-contrib-9.1.prerm: 10: .: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-contrib-9.1 (--remove):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 postgresql-client-9.1
 postgresql-9.1
 postgresql-contrib-9.1
```

After editing the file, is there anything I need to do? update or anything like that?

---

### Post by matt_symes on 2013-02-23
Hi> 

After editing the file, is there anything I need to do? update or anything like that?

It can't hurt to upate after. Be careful while editing the file. You dont want to make the situation worse.

Kind regards

---

### Post by schragge on 2013-02-23
If you want to reinstall all packages whose names start with *postgresql-* then this
```
sudo aptitude reinstall postgresql-\*
```
should be either
```
sudo aptitude reinstall \~n^postgresql-
```
or
```
sudo apt-get --reinstall install ^postgresql-
```

---

### Post by Scrumps on 2013-03-06
Eh, I had issues similar to this pop up again today after removing the entries from that file. This was doing a apt-get upgrade
> root@server:~# apt-get cleanroot@server:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up update-notifier-common (0.126) ...
ERROR:root:code for hash md5 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type md5
ERROR:root:code for hash sha1 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type sha1
ERROR:root:code for hash sha224 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type sha224
ERROR:root:code for hash sha256 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type sha256
ERROR:root:code for hash sha384 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type sha384
ERROR:root:code for hash sha512 was not found.
Traceback (most recent call last):
  File "/usr/lib/python2.7/hashlib.py", line 139, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/lib/python2.7/hashlib.py", line 91, in __get_builtin_constructor
    raise ValueError('unsupported hash type ' + name)
ValueError: unsupported hash type sha512
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 30, in <module>
    from datetime import datetime
ImportError: No module named datetime
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 16, in <module>
    from xml.parsers.expat import ExpatError
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: No module named pyexpat


Original exception was:
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 30, in <module>
    from datetime import datetime
ImportError: No module named datetime
dpkg: error processing update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.


dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 update-notifier-common
 flashplugin-installer
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)




---

### Post by matt_symes on 2013-03-07
Hi

Try this

```
sudo rm -rf /var/lib/apt/lists/*
```

Kind regards

---

