---
title: "python 2.5 and elementtree dont work"
date: 2007-04-09
forum: Programming Talk
---

### Post by earobinson on 2007-04-09
Im trying to get the google gdata-python-client to work for a program Im writing the problem is that it used elementtree, now I thought that elementtree I have manualy installed it and it still dont seem to work, Whenever I try the following code in the terminal I get the following error.

```
earobinson@NaN:/media/data/dev/gdata-python-client/samples/calendar$ python
Python 2.5.1c1 (release25-maint, Apr  6 2007, 22:02:36) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from elementtree import ElementTree
```
And the error
> Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named elementtree


Any help would be great!

Edid: Oh ya the computer is a Feistybox!

---

### Post by pmasiar on 2007-04-09
looks like manual install was not successful :-)

IIRC Feisty is coming with Python2.5, which includes elementtree - you may want to get to feisty soon - like beta :-)

If not, you need to install ET properly.

---

### Post by earobinson on 2007-04-09
Wow stupid me I forgot to mention that im running fistey,

> If not, you need to install ET properly. How would I go about doing this?

---

### Post by pmasiar on 2007-04-09
I can see in OP that you have Python2.5. According to [this](http://packages.debian.org/unstable/python/python-elementtree), ET should be installed. Question is, why it is not. Strange...

Did you made some changes in path? can you see ET somewhere in /url/lib/python2.5?

---

### Post by brentoboy on 2007-04-09
I'm having a similar problem with a different script.  

I found some info here that might help:
[http://effbot.org/zone/element-index.htm](http://effbot.org/zone/element-index.htm)

it says to change this...
```

from elementtree.ElementTree import Element, ElementTree
import elementtree.ElementTree as ET

```

to this...
```

from xml.etree.ElementTree import Element, ElementTree # python 2.5
import xml.etree.ElementTree as ET # python 2.5

```

when declaring the library.

But, after fixing that, my old error:
```

Traceback (most recent call last):
  File "/usr/local/bin/dirmonitor", line 18, in <module>
    from elementtree.ElementTree import Element, ElementTree
ImportError: No module named elementtree.ElementTree

```

changes to a much more drastic error:
```

*** glibc detected *** python: double free or corruption (out): 0x0827f4b8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e677cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e6ae30]
/var/lib/python-support/python2.5/_fam.so(_fam_event_del+0x51)[0xb79e86a1]
python(PyEval_EvalFrameEx+0xadb)[0x80c390b]
python(PyEval_EvalFrameEx+0x6135)[0x80c8f65]
python(PyEval_EvalCodeEx+0x775)[0x80c9d65]
python(PyEval_EvalCode+0x57)[0x80c9dd7]
python(PyRun_FileExFlags+0xf8)[0x80e91d8]
python(PyRun_SimpleFileExFlags+0x187)[0x80e9467]
python(Py_Main+0x9c0)[0x8059330]
python(main+0x22)[0x8058862]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7e15ebc]
python[0x80587b1]
======= Memory map: ========
08048000-0813f000 r-xp 00000000 08:02 7389965    /usr/bin/python2.5
0813f000-08164000 rw-p 000f6000 08:02 7389965    /usr/bin/python2.5
08164000-08455000 rw-p 08164000 00:00 0          [heap]
b7800000-b7821000 rw-p b7800000 00:00 0 
b7821000-b7900000 ---p b7821000 00:00 0 
b7982000-b798d000 r-xp 00000000 08:02 7241792    /lib/libgcc_s.so.1
b798d000-b798e000 rw-p 0000a000 08:02 7241792    /lib/libgcc_s.so.1
b798e000-b7997000 r-xp 00000000 08:02 7275459    /lib/tls/i686/cmov/libnss_files-2.5.so
b7997000-b7999000 rw-p 00008000 08:02 7275459    /lib/tls/i686/cmov/libnss_files-2.5.so
b7999000-b79a1000 r-xp 00000000 08:02 7275461    /lib/tls/i686/cmov/libnss_nis-2.5.so
b79a1000-b79a3000 rw-p 00007000 08:02 7275461    /lib/tls/i686/cmov/libnss_nis-2.5.so
b79a3000-b79b6000 r-xp 00000000 08:02 7275456    /lib/tls/i686/cmov/libnsl-2.5.so
b79b6000-b79b8000 rw-p 00012000 08:02 7275456    /lib/tls/i686/cmov/libnsl-2.5.so
b79b8000-b79ba000 rw-p b79b8000 00:00 0 
b79ba000-b79c1000 r-xp 00000000 08:02 7275457    /lib/tls/i686/cmov/libnss_compat-2.5.so
b79c1000-b79c3000 rw-p 00006000 08:02 7275457    /lib/tls/i686/cmov/libnss_compat-2.5.so
b79d1000-b79d8000 r-xp 00000000 08:02 7389514    /usr/lib/libfam.so.0.0.0
b79d8000-b79d9000 rw-p 00006000 08:02 7389514    /usr/lib/libfam.so.0.0.0
b79df000-b79e5000 r-xp 00000000 08:02 7553529    /usr/lib/python2.5/lib-dynload/array.so
b79e5000-b79e7000 rw-p 00006000 08:02 7553529    /usr/lib/python2.5/lib-dynload/array.so
b79e7000-b79ea000 r-xp 00000000 08:02 7818699    /usr/lib/python-support/python-fam/python2.5/_fam.so
b79ea000-b79eb000 rw-p 00002000 08:02 7818699    /usr/lib/python-support/python-fam/python2.5/_fam.so
b79eb000-b7a26000 r--p 00000000 08:02 7455626    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7a26000-b7a35000 r-xp 00000000 08:02 7241766    /lib/libbz2.so.1.0.3
b7a35000-b7a36000 rw-p 0000f000 08:02 7241766    /lib/libbz2.so.1.0.3
b7a37000-b7a3e000 r--s 00000000 08:02 1409025    /usr/lib/gconv/gconv-modules.cache
b7a3e000-b7a42000 r-xp 00000000 08:02 7553553    /usr/lib/python2.5/lib-dynload/zlib.so
b7a42000-b7a44000 rw-p 00003000 08:02 7553553    /usr/lib/python2.5/lib-dynload/zlib.so
b7a44000-b7a4a000 r-xp 00000000 08:02 7555329    /usr/lib/python2.5/lib-dynload/bz2.so
b7a4a000-b7a4c000 rw-p 00005000 08:02 7555329    /usr/lib/python2.5/lib-dynload/bz2.so
b7a4c000-b7a6f000 r-xp 00000000 08:02 7554574    /usr/lib/python2.5/site-packages/_xmlplus/parsers/pyexpat.so
b7a6f000-b7a72000 rw-p 00023000 08:02 7554574    /usr/lib/python2.5/site-packages/_xmlplus/parsers/pyexpat.so
b7a72000-b7b14000 rw-p b7a72000 00:00 0 
b7b14000-b7b19000 r-xp 00000000 08:02 7553541    /usr/lib/python2.5/lib-dynload/operator.so
b7b19000-b7b1a000 rw-p 00005000 08:02 7553541    /usr/lib/python2.5/lib-dynload/operator.so
b7b1a000-b7b5b000 rw-p b7b1a000 00:00 0 
b7b5b000-b7b6f000 r-xp 00000000 08:02 7555295    /usr/lib/python2.5/lib-dynload/_ctypes.so
b7b6f000-b7b71000 rw-p 00014000 08:02 7555295    /usr/lib/python2.5/lib-dynload/_ctypes.so
b7b71000-b7b84000 r-xp 00000000 08:02 7391232    /usr/lib/libz.so.1.2.3
b7b84000-b7b85000 rw-p 00012000 08:02 7391232    /usr/lib/libz.so.1.2.3
b7b85000-b7caf000 r-xp 00000000 08:02 7454984    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7caf000-b7cc3000 rw-p 00129000 08:02 7454984    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7cc3000-b7cc7000 rw-p b7cc300Aborted (core dumped)

```

the python script in question looks like this:
```

#!/usr/bin/env python
# encoding: utf-8
#
# Copyright (c) 2006 Dag Sverre Seljebotn
# Contact: dagss@student.matnat.uio.no / dss@fredtun.no
#
# This program is licensed under version 2 of the GNU General Public License.
# See the file COPYING for details, or http://www.gnu.org/copyleft/gpl.html
#

import _fam
import sys, time, select, signal, errno, os, stat
import pwd, grp

from xml.etree.ElementTree import Element, ElementTree # python 2.5
import xml.etree.ElementTree as ET # python 2.5

#from elementtree.ElementTree import Element, ElementTree
#import elementtree.ElementTree as ET

#from lxml.etree import Element, ElementTree
#import lxml.etree as ET

def _(s):
	"""Dummy function making it easier to introduce i18n later."""
	return s

class FamMonitor:
	"""Just a little more friendly wrapper around FAM. Mostly borrowed from the example
	bundled with python-fam."""

	#
	# public part
	#
	def __init__(self, config_func):
		"""
		@param config_func: A function taking this object as a parameter. It will be called
			every time a reload of configuration is required (in the beginning, and when
			recieving SIGUSR1).
		"""
		self.famconn = None
		self.signals = []
		self.listener_to_dir = {}
		self.config_func = config_func
		
		for signum in [signal.SIGINT, signal.SIGUSR1, signal.SIGUSR2]:
			signal.signal(signum, self.__collect_signal)
		
		self.signal_handlers = {
			signal.SIGINT  : self.__sigintr,
			signal.SIGUSR1 : self.__sigusr1,
			signal.SIGUSR2 : self.__sigusr2,
		}

	def listen_loop(self):
		self.config_func(self)
		self.__connect_all()
		try:
			while True:
				# Any signals queued?
				while len(self.signals) > 0:
					signum, frame = self.signals.pop(0)
					if self.signal_handlers[signum](signum, frame): return
			
				# Wait until more events are ready
				try:
					select.select([self.famconn], [], [])
				except select.error, er:
					errnumber, strerr = er
					if errnumber == errno.EINTR:
						continue
					else:
						raise Exception(strerr)
					
				# Execute events
				while self.famconn.pending():
					event = self.famconn.nextEvent()
					event.userData.execute(event)
		finally:
			self.__disconnect_all()
	
	def add_listener(self, dirname, listener):
		d = FamMonitor.Dir(dirname, listener)
		self.listener_to_dir[listener] = d
		if self.famconn is not None:
			d.connect(self.famconn)
	
	def remove_listener(self, listener):
		self.listener_to_dir[listener].disconnect()
		del self.listener_to_dir[listener]
	
	def has_listeners(self, dirname):
		return dirname in self.dirs.keys()
			
	def clear(self):
		for dirinfo in self.listener_to_dir.values():
			dirinfo.disconnect()
		self.listener_to_dir = {}

	#
	# private part
	#
	class Dir:
		def __init__(self, dirname, listener):
			self.dirname = dirname
			self.listener = listener
			self.monitor = None
		def connect(self, famconn):
			if self.monitor is None:
				self.monitor = famconn.monitorDirectory(self.dirname, self)
		def disconnect(self):
			if self.monitor is not None:
				self.monitor.cancelMonitor()
				self.monitor = None
		def execute(self, event):
			self.listener.notify(self.dirname, event)
		

	def __initconnection(self):
		if self.famconn is None:
			self.famconn = _fam.open()
	
	def __connect_all(self):
		self.__initconnection()
		for dirinfo in self.listener_to_dir.values():
			dirinfo.connect(self.famconn)
	
	def __disconnect_all(self):
		for dirinfo in self.listener_to_dir.values():
			dirinfo.disconnect()
			
		self.famconn.close()
		self.famconn = None
	
	def __sigintr(self, signum, frame):
		return True
	
	def __sigusr2(self, signum, frame):
		return True

	def __sigusr1(self, signum, frame):
		self.__disconnect_all()
		time.sleep(1)
		self.config_func(self)
		self.__connect_all()

	def __collect_signal(self, signum, frame):
		self.signals.append((signum, frame))



class RecursiveDirListener(object):
	def __init__(self):
		self.children = {}

	def notify(self, dirname, event):
		filename = event.filename
		if filename == dirname: return # is about the parent dir (often Exists), our parent will pick it up
		
		target = os.path.join(dirname, filename)
		code = event.code
		
		# isdir does not follow symlinks
		if (code == _fam.Exists or code == _fam.Created) and \
				os.path.isdir(target) and not os.path.islink(target) and \
				not filename in self.children.keys():
			# Child directory listed/created, add listener to it
			child = self.create_child_listener()
			self.get_monitor().add_listener(target, child)
			self.children[filename] = child
		elif code == _fam.Deleted and filename in self.children.keys():
			# Child directory removed, remove its listener recursively
			self.children[filename].unregister()
			del self.children[filename]
	
	def unregister(self):
		self.get_monitor().remove_listener(self)
		for child in self.children.values():
			child.unregister()

class MonitorListener(RecursiveDirListener):
	def __init__(self, root):
		super(MonitorListener, self).__init__()
		self.root = root

	def notify(self, dirname, event):
		super(MonitorListener, self).notify(dirname, event)
		if dirname == event.filename: return
		
		code = event.code
		if code == _fam.Exists or code == _fam.Created or code == _fam.Changed:
			target = os.path.join(dirname, event.filename)
			fileinfo = os.lstat(target)
			self.root.rules.apply_to(target, fileinfo, self.root.logger)
	
	def get_monitor(self):
		return self.root.monitor
	
	def create_child_listener(self):
		return MonitorListener(self.root)
	
class RootMonitorListener(MonitorListener):
	def __init__(self, dirname, rules, monitor, logger):
		super(RootMonitorListener, self).__init__(self)
		self.rules = rules
		self.monitor = monitor
		self.logger = logger
	
class ChmodRule:
	def __init__(self, perms):
		self.perms = perms
	def apply_to(self, actions):
		actions.perms = self.perms
	def __repr__(self): return "ChmodRule(%o)" % self.perms

class UserRule:
	def __init__(self, uid):
		self.uid = uid
	def apply_to(self, actions):
		actions.uid = self.uid
	def __repr__(self): return "UserRule(%d)" % self.uid

class GroupRule:
	def __init__(self, gid):
		self.gid = gid
	def apply_to(self, actions):
		actions.gid = self.gid
	def __repr__(self): return "GroupRule(%d)" % self.gid

class TypeSwitchRule:
	def __init__(self):
		# These lists are filled in directly by the client of the object
		self.filerules = []
		self.dirrules = []
		self.nonexecrules = []
		self.execrules = []
		
	def apply_to(self, fileactions):
		def apply_all(rules, fileactions):
			for rule in rules:
				rule.apply_to(fileactions)

		mode = fileactions.fileinfo.st_mode
		if stat.S_ISDIR(mode):
			apply_all(self.dirrules, fileactions)
		else:
			apply_all(self.filerules, fileactions)
			if (stat.S_IEXEC & mode) != 0:
				apply_all(self.execrules, fileactions)
			else:
				apply_all(self.nonexecrules, fileactions)
	def __repr__(self):
		return """TypeSwitchRule:
dir: %s
file %s
exec: %s
nonexec: %s
""" % (repr(self.dirrules), repr(self.filerules), repr(self.execrules), repr(self.nonexecrules))

class RulesProcessor(object):
	"""
	Specifies the rules to apply to a given directory tree.
	
	Symbolic links are not followed.
	"""
	class Actions:
		def __init__(self, filename, fileinfo):
			self.perms = None
			self.uid = None
			self.gid = None
			self.filename = filename
			self.fileinfo = fileinfo
			
		def apply_actions(self, logger):
			if self.perms is not None and stat.S_IMODE(self.fileinfo.st_mode) != self.perms:
				logger.log('chmod %o "%s"' % (self.perms, self.filename))
				os.chmod(self.filename, self.perms)
			if self.uid is not None or self.gid is not None:
				uid = self.uid
				gid = self.gid
				if uid is None: uid = self.fileinfo.st_uid
				if gid is None: gid = self.fileinfo.st_gid
				if uid != self.fileinfo.st_uid or gid != self.fileinfo.st_gid:
					logger.log('chown %d:%d "%s"' % (uid, gid, self.filename))
					os.chown(self.filename, uid, gid)
	
	def __init__(self, children):
		self.children = children
	
	def apply_to(self, filename, fileinfo, logger):
		if stat.S_ISLNK(fileinfo.st_mode): return # ignore links
		
		fileactions = RulesProcessor.Actions(filename, fileinfo)
		
		for child in self.children:
			child.apply_to(fileactions)
		fileactions.apply_actions(logger)
	
	def __repr__(self):
		return "RulesProcessor (%s)" % self.children
	
class ConfigParseException(ValueError):
	def __init__(self, msg):
		ValueError.__init__(self, msg)

class Configuration(object):

	NS = "http://www.fredtun.no/xmlns/dir-monitor-config/0.2"
	ROOT_ELEM = "dir-monitor-config"
	DIR_ELEM = "dir"
	ENFORCE_ELEM = "enforce"
	LOC_ATTR = "loc"
	OWNER_ATTR = "owner"
	GROUP_ATTR = "group"
	PERMISSIONS_ATTR = "permissions"
	
	TYPESWITCH_ELEM = "type-switch"
	DIRECTORY_ELEM = "directory"
	FILE_ELEM = "file"
	EXECFILE_ELEM = "executable-file"
	NONEXECFILE_ELEM = "normal-file"

	YES = "yes"
	NO = "no"
	
	NS_ERROR = _('Element not part of the namespace "%s"')

	def __init__(self, configfile, logger):
		self.configfile = configfile
		self.logger = logger
	
	def nserror(self):
		self.synerror(self.NS_ERROR % self.NS)
	
	def qf(self, elemname):
		return "{%s}%s" % (self.NS, elemname)
	
	def iselem(self, tagname, element):
		return tagname == self.qf(element.tag)
	
	def elemjump(self, jumpmap, element, *args, **kwargs):
		"""Jump to different functions depending on the jumpmap (a map from unqualified element names
		to functions taking the extra args as args and possibly returning a value). If there isn't
		a match, a descriptive exception is raised."""
		tagname = element.tag
		if not tagname.startswith("{%s}" % self.NS):
			self.nserror()
		tagname = tagname[len(self.NS) + 2:]
		names = jumpmap.keys()
		if not tagname in names:
			commanames = '", "'.join(names[0:-1])
			self.synerror(_('Expected "%s" or "%s" element, got "%s"' % (commanames, names[-1], tagname)))
		else:
			return jumpmap[tagname](*args, **kwargs)
	
	def check_config(self):
		self.load_config()

	def load_config_to(self, monitor):
		monitor.clear()
		for loc, rule in self.load_config():
			rootlistener = RootMonitorListener(loc, rule, monitor, self.logger)
			monitor.add_listener(loc, rootlistener)

	def load_config(self):
		"""Returns a list of (dir, rulesprocessor)."""
		
		try:
			tree = ET.parse(self.configfile)
		except SyntaxError:
			self.synerror(_('XML syntax error: "%s"') % self.configfile)
		except:
			self.synerror(_('Could not open: "%s"') % self.configfile)
			
		root = tree.getroot()
		self.assertelem(self.ROOT_ELEM, root)
		result = []
		for directory in root:
			self.assertelem(self.DIR_ELEM, directory)
			loc = directory.get(self.LOC_ATTR)
			ruleelems = directory.getchildren()
			childrules = []
			for rule in directory:
				childrules.extend(self.parse_rule(rule))
			result.append((loc, RulesProcessor(childrules)))
		return result
			
	def synerror(self, msg):
		raise ConfigParseException(msg)
	
	def synassert(self, condition, msg):
		if not condition: synerror(msg)
	
	def assertelem(self, expected, elem):
		if self.iselem(expected, elem):
			self.synerror(_("Element %s found but %s expected") % (elem.tag, expected))
	
	def bool_attr(self, elem, name, empty_allowed=True):
		value = elem.get(name)
		if value is None:
			if empty_allowed: return None
			else: self.synerror(_("Attribute %s missing on element %s") % (name, elem.tag))
		if value == self.YES:
			return True
		elif value == self.NO:
			return False
		else:
			self.synerror(_('Attribute %s on element %s must be either "yes" or "no"') % (name, elem.tag))

	def parse_rule(self, elem):
		"""Parses any rule element and returns a list of XXXRule objects corresponding to it."""
		
		def enforce():
			result = []
			perms = elem.get(self.PERMISSIONS_ATTR, None)
			owner = elem.get(self.OWNER_ATTR, None)
			group = elem.get(self.GROUP_ATTR, None)
			if perms is not None:
				result.append(ChmodRule(self.parse_perm_str(perms)))
			if owner is not None:
				result.append(UserRule(self.lookup_uid(owner)))
			if group is not None:
				result.append(GroupRule(self.lookup_group(group)))
			return result
		
		def typeswitch():
			switch = TypeSwitchRule()
			
			def directory(): return switch.dirrules
			def fileel(): return switch.filerules
			def execfileel(): return switch.execrules
			def nonexecfileel(): return switch.nonexecrules
			
			for portion in elem:
				childlist = self.elemjump({
						self.DIRECTORY_ELEM: directory,
						self.FILE_ELEM: fileel,
						self.EXECFILE_ELEM: execfileel,
						self.NONEXECFILE_ELEM: nonexecfileel}, portion)
				for rule in portion:
					childlist.extend(self.parse_rule(rule))
			return [switch]
			
		return self.elemjump({self.ENFORCE_ELEM: enforce, self.TYPESWITCH_ELEM: typeswitch}, elem)
		
		
	def parse_perm_str(self, modestr):
		"""Parses UNIX permission strings (example: rwxr-x-wx) and returns UNIX mode int."""
		ERROR = _('Invalid mode string: %s') % modestr
		
		CHARS = 'rwxrwxrwx'
		BITS = [stat.S_IRUSR, stat.S_IWUSR, stat.S_IXUSR, stat.S_IRGRP, stat.S_IWGRP, stat.S_IXGRP, \
				stat.S_IROTH, stat.S_IWOTH, stat.S_IXOTH]
		
		self.synassert(len(modestr) == 9, ERROR)
		normal = 0
		
		for ch, onch, bit in zip(modestr, CHARS, BITS):
			if ch == onch:
				normal |= bit
			else:
				self.synassert(ch == '-', ERROR)

		return normal
	
	def lookup_uid(self, name):
		if name.isdigit(): return int(name)
		else:
			try:
				return pwd.getpwnam(name).pw_uid
			except:
				self.synerror(_('Unknown username supplied (or could not access user database): "%s"') % name)
			
	def lookup_group(self, name):
		if name.isdigit(): return int(name)
		else:
			try:
				return grp.getgrnam(name).gr_gid
			except:
				self.synerror(_('Unknown group supplied (or could not access group database): "%s"') % name)
	
	
DEBUG = False

class Logger:
	def log(self, s):
		print s

def quit(ex, errnum):
	if DEBUG: raise ex
	else: sys.exit(errnum)

try:
	config = Configuration(sys.argv[1], Logger())
	config.check_config()
except ConfigParseException, e:
	print "Cannot start, there is an error in the config file:"
	print "   " + str(e)
	if DEBUG:
		raise e
	else:
		sys.exit(1)

f = FamMonitor(config.load_config_to)
f.listen_loop()

```

and my config file (if that helps) looks like this (this is the file who's xml stream is unraveled by the elementtree object):
```

<?xml version="1.0" encoding="utf-8"?>
<dir-monitor-config xmlns="http://www.fredtun.no/xmlns/dir-monitor-config/0.2">
	<dir loc="/media/hdb1/share">
		<enforce owner="nobody" group="nogroup"/>
		<type-switch>
			<directory>
				<enforce permissions="rwxrwxrwx"/>
			</directory>
			<file>
				<enforce group="nogroup"/>
			</file>
			<normal-file>
				<enforce permissions="rw-rw-rw-"/>
			</normal-file>
			<executable-file>
				<enforce permissions="rw-rw-rw-"/>
			</executable-file>
		</type-switch>
	</dir>
</dir-monitor-config>

```

Is there anyone out there who knows enough about the new changes in python to help me?  By the way, this script worked in dapper, and edgy (so long as I added the pythion-fam and python-elementtree pachages).

thanks in advance for any help...

---

### Post by pmasiar on 2007-04-09
> **brentoboy said:**
> I found some info here that might help:
[http://effbot.org/zone/element-index.htm](http://effbot.org/zone/element-index.htm)

it says to change this...
```

from elementtree.ElementTree import Element, ElementTree
import elementtree.ElementTree as ET

```

to this...
```

from xml.etree.ElementTree import Element, ElementTree # python 2.5
import xml.etree.ElementTree as ET # python 2.5

```


You are switching between different libraries. Can you try just the "import...." statement on python shell if it will fail or not? if libraries are present?

I did not checked - do all these libraries have exactly same API?

---

### Post by earobinson on 2007-04-10
Thanks! Worked perfectly!

---

### Post by brentoboy on 2007-04-10
Yes, they all have the same API's
When they were added to the "official" python, they were put into the "proper" place in the object hierarchy rather than the place where it was placed by the guy who wrote it when it was just a "startup" project.

anyway, at this point, I am convinced that my error ends up craping out in the python-fam module, not the elementtree object(s).

I got the "bad" error I listed above when I finally sorted out the element tree object name issue.

But, because I don't know enough about python to be sure about doing any finger pointing and bug reporting, I just moved myself back to edgy where it wasn't a problem.

-brent

---

