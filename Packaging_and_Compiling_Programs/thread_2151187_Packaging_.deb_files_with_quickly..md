---
title: "Packaging .deb files with quickly."
date: 2013-06-03
forum: Packaging and Compiling Programs
---

### Post by sudo san on 2013-06-03
Hi, I am using quickly to create a command line application I am testing the app with:
```
quickly run
```

All runs fine until I use the commands:
```
quickly package
cd ..
sudo dpkg -i my_application.deb
```

The app is created just fine but when run, it issues the command included with the template (which I commented out):
```
# print _("I'm launched and my args are: %s") % (" ".join(args))
```

How can I get my code to run?
Here are the three important files, I only edited the __inti__.py file. If anyone requires any more info, please ask. Thanks in advance. :)

__init__.py:
```
import loggingimport optparse
import os
import lsb_release


import gettext
from gettext import gettext as _
gettext.textdomain('pru')


from pru import pruconfig


LEVELS = (  logging.ERROR,
            logging.WARNING,
            logging.INFO,
            logging.DEBUG,
            )


def main():
    version = pruconfig.__version__
    # Support for command line options.
    usage = _("pru [options]")
    parser = optparse.OptionParser(version="%%prog %s" % version, usage=usage)
    parser.add_option('-d', '--debug', dest='debug_mode', action='store_true',
        help=_('Print the maximum debugging info (implies -vv)'))
    parser.add_option('-v', '--verbose', dest='logging_level', action='count',
        help=_('set error_level output to warning, info, and then debug'))
    # exemple of silly CLI option
    parser.add_option("-f", "--foo", action="store", dest="foo",
                      help=_("foo should be assigned to bar"))
    parser.set_defaults(logging_level=0, foo=None)
    (options, args) = parser.parse_args()


    # set the verbosity
    if options.debug_mode:
        options.logging_level = 3
    logging.basicConfig(level=LEVELS[options.logging_level], format='%(asctime)s %(levelname)s %(message)s')




    # this is the easter egg (:
    if options.foo == 'bar':
        logging.warning(_('easter egg found'))
        print("Schweet")


    # Begin code.
    # print _("I'm launched and my args are: %s") % (" ".join(args))


    # Begin script.
    
    # Assign ubuntu release name into 'release'.
    release = lsb_release.get_distro_information()['CODENAME']


    # Assign usefull information into variables.
    if release == "precise":
        release_name = "Precise Pangolin 12.04"
        upgrading_release = "Quantal Quetzal 12.10"
        upgrading_release_codename = "quantal"


    elif release == "quantal":
        release_name = "Quantal Quetzal 12.10"
        upgrading_release = "Raring Ringtail 13.04"
        upgrading_release_codename = "raring"


    elif release == "raring":
        release_name = "Raring Ringtail 13.04"
        upgrading_release = "Saucy Salamander 13.10"
        upgrading_release_codename = "saucy"




    # yorn is short for yes or no.
    # Asking if want to upgrade first and giving information.


    print("You are using Ubuntu release: " + release_name)
    yorn = raw_input("Are you sure you want to upgrade from " + release_name + " to " + upgrading_release + " [Y/n]? ")


    if (yorn.upper()=="Y"):
        print("This may take a while, sit back with a cup of coffee and some biscuits,\
 now changing repositories.")


        # Changing repos.
        os.system("sudo sed -i 's/" + release + "/" + upgrading_release_codename + "/g' '/etc/apt/sources.list'")


        for i in range(1):
            # Updating repos.
            print("Now updating repositories")
            os.system("sudo apt-get update -qq")


            for i in range(1):
                # Upgrading packages.
                print("Now upgrading packages, prepare for lots of text!")
                os.system("sudo apt-get dist-upgrade -f -y")


                print("Now checking all packages installed correctly......")


                for i in range(1):
                    os.system("sudo apt-get install -f -y && sudo dpkg --configure -a")


                    for i in range(1):
                        os.system("sudo update-grub")


                        # Asking if want to reboot.
                        yorn_2 = raw_input("You are now ready to reboot into the upgraded system, do you want to reboot now [Y/n]? ")
                        if (yorn_2.upper()=='Y'):
                            os.system("sudo reboot")


                        elif (yorn_2.upper()=='N'):
                            print("Ok, Bye!")






    elif (yorn.upper()=="N"):
        print("Ok then, Bye!")


    else:
        print("Invalid input, please enter y/n or Y/N")




    logging.debug(_('end of prog'))




if __name__ == "__main__":
    main()
```

my_appconfig.py:
```
# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-### BEGIN LICENSE
# This file is in the public domain
### END LICENSE


# THIS IS Pru CONFIGURATION FILE
# YOU CAN PUT THERE SOME GLOBAL VALUE
# Do not touch unless you know what you're doing.
# you're warned :)


__all__ = [
    'project_path_not_found',
    'get_data_file',
    'get_data_path',
    ]


# Where your project will look for your data (for instance, images and ui
# files). By default, this is ../data, relative your trunk layout
__pru_data_directory__ = '../data/'
__license__ = ''
__version__ = 'VERSION'


import os


import gettext
from gettext import gettext as _
gettext.textdomain('pru')


class project_path_not_found(Exception):
    """Raised when we can't find the project directory."""




def get_data_file(*path_segments):
    """Get the full path to a data file.


    Returns the path to a file underneath the data directory (as defined by
    `get_data_path`). Equivalent to os.path.join(get_data_path(),
    *path_segments).
    """
    return os.path.join(get_data_path(), *path_segments)




def get_data_path():
    """Retrieve pru data path


    This path is by default <pru_lib_path>/../data/ in trunk
    and /usr/share/pru in an installed version but this path
    is specified at installation time.
    """


    # Get pathname absolute or relative.
    path = os.path.join(
        os.path.dirname(__file__), __pru_data_directory__)


    abs_data_path = os.path.abspath(path)
    if not os.path.exists(abs_data_path):
        raise project_path_not_found


    return abs_data_path
```

my_app:
```
#!/usr/bin/python# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE


import os
import sys


# Add project root directory (enable symlink, and trunk execution).
PROJECT_ROOT_DIRECTORY = os.path.abspath(
    os.path.dirname(os.path.dirname(os.path.realpath(sys.argv[0]))))


python_path = []
if os.path.abspath(__file__).startswith('/opt'):
    syspath = sys.path[:] # copy to avoid infinite loop in pending objects
    for path in syspath:
        opt_path = path.replace('/usr', '/opt/extras.ubuntu.com/pru')
        python_path.insert(0, opt_path)
        sys.path.insert(0, opt_path)
if (os.path.exists(os.path.join(PROJECT_ROOT_DIRECTORY, 'pru'))
    and PROJECT_ROOT_DIRECTORY not in sys.path):
    python_path.insert(0, PROJECT_ROOT_DIRECTORY)
    sys.path.insert(0, PROJECT_ROOT_DIRECTORY)
if python_path:
    os.putenv('PYTHONPATH', "%s:%s" % (os.getenv('PYTHONPATH', ''), ':'.join(python_path))) # for subprocesses    os.putenv('PYTHONPATH', PROJECT_ROOT_DIRECTORY) # for subprocesses


import pru
pru.main()
```

---

