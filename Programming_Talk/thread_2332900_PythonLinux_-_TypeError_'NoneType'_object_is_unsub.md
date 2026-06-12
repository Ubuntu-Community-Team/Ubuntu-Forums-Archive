---
title: "Python/Linux - TypeError: 'NoneType' object is unsubscriptable"
date: 2016-08-05
forum: Programming Talk
---

### Post by kurtarries on 2016-08-05
Hi,


I am trying to run the following script in linux:
[I]/opt/commissioning/bin/configure_database_upgrade -c /var/tclncna8_cluster_info.txt -s /opt/skynet/dca/dca-install/config/tclncna8_280716153454.xml -v /var/netact/tclncna8_vmware_vconf.yml

[/I]The error that occurs exists in a Python script. This is output of running that script: 

```
 Traceback (most recent call last):
  File "/opt/commissioning/bin/configure_database_upgrade", line 284, in <module>
    OdgNzdtUpgConf().main()
  File "/opt/commissioning/bin/configure_database_upgrade", line 30, in main
    self.args = Arguments()
  File "/opt/commissioning/bin/configure_database_upgrade", line 93, in __init__
    self.dbdatadsname     = vconf.getVmByType('db').getDiskByScsiId(3)['datastore_name']
TypeError: 'NoneType' object is unsubscriptable 
```

So, I opened the script "configure_database_upgrade" which is coded in python. It is pasted below:

```
 #!/usr/bin/python
from sys import argv, stderr, exit
from getopt import gnu_getopt
from os import rename, mkdir
from os.path import exists, isdir
from socket import socket, AF_INET, SOCK_DGRAM
from fcntl import ioctl
from array import array
from struct import pack, unpack
from re import compile, sub
from pipes import quote
from subprocess import call
from shlex import split


VERBOSE      = False
TEMPLATE_DIR = '/opt/commissioning/template'
CONF_DIR     = '/etc/opt/commissioning/conf'
CONF_FILES   = [
   'DBnodeUpgradeConf.txt',
   'DBnodeCopyConf.xml',
   'DBnodeCopySmConf.xml',
   'DBnodeActivate.xml',
   'odg-nzdt-upg.conf'
]


class OdgNzdtUpgConf:
   def main(self):
      if exists('/etc/redhat-release'):
         self.checkDependencies()
      self.args = Arguments()
      cff = ConfigurationFileFactory()
      cff.setHandler('.txt', self.applyTextConfig)
      cff.setHandler('.conf', self.applyTextConfig)
      cff.setHandler('.xml', self.asIs)
      for fn in CONF_FILES:
         cff.make(fn)
   def checkDependencies(self):
      rv = call("rpm -q python python-libs python-lxml python-paramiko PyYAML --qf ''", shell=True)
      if rv != 0:
         print >>stderr, "ERROR: missing dependencies"
         print >>stderr, "Please install the missing packages and re-execute %s" % argv[0]
         exit(rv)
   def applyTextConfig(self, l):
      for k, v in [
         ('SYSTEM_NAME',                  self.args.systemname),
         ('ORG_DB_DS_NAME',               self.args.dbdatadsname),
         ('ORG_REDO_DS_NAME',             self.args.dbredodsname),
         ('ORG_ARCH_DS_NAME',             self.args.dbarchdsname),
         ('UPGR_ARCH_DS_NAME',            self.args.dbarchdsname),
         ('ORG_BACKUP_DS_NAME',           self.args.backupdsname),
         ('DATASTORE_FOR_DEPLOYED_IMAGE', self.args.newdbdatastore),
         ('VCENTER_IP',                   self.args.vcenterip),
         ('VCENTER_PWD',                  self.args.vcenterpassword),
         ('DATACENTER_NAME',              self.args.datacentername),
         ('CLUSTER_NAME',                 self.args.clustername),
         ('RESOURCE_POOL_NAME',           self.args.resourcepoolname),
         ('VM_ROOT_PASS',                 self.args.rootpassword),
         ('DATABASE_NODE',                self.args.unifydbhostname),
         ('SELFMON_NODE',                 self.args.selfmonhostname),
         ('WAS_DMGR',                     self.args.dmgrhostname),
         ('ONEPM_DSS1',                   self.args.onepmdss1name),
         ('ONEPM_NAS1',                   self.args.onepmnas1name),
         ('NFS_SERVER',                   self.args.nfsservername),
      ]:
         l = sub(r'^(%s)=.*' % k, r'\1=%s' % quote(v), l)
      return l
   def applyXmlConfig(self, l):
      for k, v in [
         ('SOURCE_HOSTNAME',              self.args.unifydbhostname),
         ('ROOT_PASSWORD',                self.args.rootpassword),
         ('DESTINATION_VM',               self.args.destinationip),
         ('SOURCE_VM',                    self.args.sourceip),
      ]:
         l = sub(r'\b%s\b' % k, v, l)
      return l
   def asIs(self, l):
      return l


class Arguments:
   def __init__(self):
      ci, unify, vconf = self.parse()
      self.systemname       = ci['SYSTEMNAME']
      self.viisname         = ci['MIS_HOSTNAME']
      self.vcenterip        = ci['VCENTER_IP']
      self.vcenterpassword  = ci['VCENTER_ROOT_PASSWORD']
      self.rootpassword     = ci['VM_PASSWORD']
      self.onepmdss1name    = ci['DSS1_NAME']
      self.onepmnas1name    = ci['NAS1_NAME']
      self.datacentername   = vconf['vcenter']['DCname']
      self.clustername      = vconf['cluster'][0]['cluster_name']
      self.resourcepoolname = vconf['res_pool'][0]['res_pool_name']
      self.newdbdatastore   = vconf.getVmByType('db')['datastore_name']
      self.dbdatadsname     = vconf.getVmByType('db').getDiskByScsiId(3)['datastore_name']
      self.dbredodsname     = vconf.getVmByType('db').getDiskByScsiId(2)['datastore_name']
      self.dbarchdsname     = vconf.getVmByType('db').getDiskByScsiId(1)['datastore_name']
      try:
         self.backupdsname     = vconf.getVmByType('db').getDiskByScsiId(8)['datastore_name']
      except TypeError:
         self.backupdsname   = "backupnotinuse"
      self.unifydbhostname  = unify.getHostnameInCrole('CPF.CROLE.DB_SERVER')
      self.selfmonhostname  = unify.getHostnameInCrole('OSS.CROLE.SELF-MONITOR')
      self.dmgrhostname     = unify.getHostnameInCrole('OSS.CROLE.WAS_DMGR')
      self.nfsservername    = unify.getHostnameInCrole('CPF.CROLE.NFS_SERVER')
      self.privnetmask      = vconf['host'][0]['vmotion_sm']
      self.privvlan         = vconf.getPgByType('pg_vMotion_Network')['vlanid']
      ipf = IpAddressFactory([host['vmotion_ip'] for host in vconf['host']])
      self.viisprivip       = ipf.next()
      self.sourceip         = ipf.next()
      self.destinationip    = ipf.next()
      nie = NetworkInterfaceEnumerator()
      self.viisprivdev      = nie.get(self.viisprivip) or nie.next()
   def parse(self):
      ci = unify = vconf = None
      opts, args = gnu_getopt(argv, 'c:s:v:n:T:D:V')
      for opt, arg in opts:
         if opt == '-c':
            ci = ClusterInfo(arg)
         elif opt == '-s':
            unify = DcaStack(arg)
         elif opt == '-v':
            vconf = VmwareVconf(arg)
         elif opt == '-T':
            global TEMPLATE_DIR
            TEMPLATE_DIR = arg.rstrip('/')
            assert exists(TEMPLATE_DIR) and isdir(TEMPLATE_DIR)
         elif opt == '-D':
            global CONF_DIR
            CONF_DIR = arg.rstrip('/')
            assert exists(CONF_DIR) and isdir(CONF_DIR)
         elif opt == '-V':
            global VERBOSE
            VERBOSE = True
         else:
            assert False
      if ci is None or unify is None or vconf is None or len(args) != 1:
         print >>stderr, "Usage: %s -c CLUSTER_INFO_FILE -s UNIFY_DCA_STACK_XML_FILE -v VMWARE_VCONF_FILE" % argv[0]
         exit(1)
      return ci, unify, vconf


class NetworkInterfaceEnumerator:
   def __init__(self):
      self.interfaces = {}
      self.lasteth = -1
      s = socket(AF_INET, SOCK_DGRAM)
      try:
         SIOCGIFCONF = 0x8912
         b = array('B', '\0' * 4096)
         l = unpack('iL', ioctl(s.fileno(), SIOCGIFCONF, pack('iL', b.buffer_info()[1], b.buffer_info()[0])))[0]
         exp = compile('eth(\d+)')
         for i in range(0, l, 40):
            ifr_name, in_family, sin_port, s_addr = unpack('<16shHL', b[i:i + 24])
            dev = ifr_name.split('\0', 1)[0]
            address = '.'.join([str((s_addr) >> (i << 3) & 0xFF) for i in range(3, -1, -1)[::-1]])
            self.interfaces[address] = dev
            m = exp.match(dev)
            if m:
               n = int(m.group(1))
               if n > self.lasteth:
                  self.lasteth = n
      finally:
         s.close()
   def get(self, address):
      return self.interfaces[address] if address in self.interfaces else None
   def next(self):
      self.lasteth += 1
      return 'eth%d' % self.lasteth


class IpAddressFactory:
   def __init__(self, ips):
      self.lastip = 0
      for ip in ips:
         self.lastip = max(self.lastip, reduce(lambda x, y: (x << 8) + y, map(int, ip.split('.'))))
   def next(self):
      self.lastip += 1
      return '.'.join([str((self.lastip) >> (i << 3) & 0xFF) for i in range(0, 4)[::-1]])


class ConfigurationFileFactory:
   def __init__(self):
      self.handlers = {}
   def setHandler(self, ext, handler):
      self.handlers[ext] = handler
   def make(self, fn):
      handler = None
      for key in self.handlers:
         if fn.endswith(key):
            handler = self.handlers[key]
            break
      if handler is None:
         raise Exception("No handler available for %s" % fn)
      src = '%s/%s_template' % (TEMPLATE_DIR, fn)
      tgt = '%s/%s' % (CONF_DIR, fn)
      with open(src) as f:
         conf = ""
         template = ""
         for l in f:
            template += l
            conf += handler(l)
      if exists(tgt):
         with open(tgt) as f:
            orig = ""
            for l in f:
               orig += l
      else:
         orig = None
      if conf != orig:
         if orig is not None:
            print "updating", tgt
            if VERBOSE:
               from difflib import unified_diff as diff
               for line in diff(orig.splitlines(), conf.splitlines(), 'original %s' % tgt, 'modified %s' % tgt):
                  print line.rstrip('\n')
            rename(tgt, '%s.prev' % tgt)
         else:
            if VERBOSE:
               from difflib import unified_diff as diff
               for line in diff(template.splitlines(), conf.splitlines(), src, tgt):
                  print line.rstrip('\n')
            print "creating", tgt
         if not exists(CONF_DIR):
            mkdir(CONF_DIR)
         with open(tgt, 'w') as f:
            f.write(conf)
      else:
         if VERBOSE:
            print "unmodified", tgt


class ClusterInfo:
   def __init__(self, fn):
      self.fn = fn
      self.dict = {}
      with open(fn) as f:
         for line in f:
            key, value = line.strip().partition('=')[::2]
            if key:
               self.dict[key] = sub(r'\\([`$])', r'\1', split(value)[0]) if value else ''
   def __getitem__(self, key):
      return self.dict[key]


class DcaStack:
   def __init__(self, fn):
      from lxml import etree as ET
      self.nsmap = {
         'dca': 'https://svne1.access.nokiasiemensnetworks.com/isource/svnroot/oss_cpf/components/skynet/dca-jar/src/main/resources/schema'
      }
      self.stack = ET.parse(fn)
   def getHostnameInCrole(self, crole):
      return self.find('/dca:dcaConfiguration/dca:nodeArchitecture/dca:nodeMapping[dca:customRoles/dca:nodeRole[@role="%s"]]/dca:nodeIds/dca:node' % crole).get('nodeName')
   def getAttributeValue(self, name):
      return self.find('/dca:dcaConfiguration/dca:attrCollection/dca:attrDefault[@attrName="%s"]/dca:value' % name).text
   def find(self, xpath):
      return self.stack.xpath(xpath, namespaces=self.nsmap)[0]


class AbstractVmwareVconf:
   def __init__(self, vconf):
      self.vconf = vconf
   def __getitem__(self, key):
      if type(self.vconf[key]) in (dict, list):
         return AbstractVmwareVconf(self.vconf[key])
      else:
         return str(self.vconf[key])


class VmwareVconf(AbstractVmwareVconf):
   def __init__(self, fn):
      from yaml import load
      with open(fn) as f:
         AbstractVmwareVconf.__init__(self, load(f))
   def getVmByType(self, vmtype):
      for vm in self.vconf['vm']:
         if 'type' in vm and vm['type'] == vmtype:
            return VmwareVconfVm(vm)
   def getPgByType(self, pgtype):
      for vds in self.vconf['vds']:
         for pg in vds['portgroup']:
            if 'portgroup_type' in pg and pg['portgroup_type'] == pgtype:
               return AbstractVmwareVconf(pg)


class VmwareVconfVm(AbstractVmwareVconf):
   def getDiskByScsiId(self, scsiid):
      for disk in self.vconf['disk']:
         if 'scsi_id' in disk and disk['scsi_id'] == scsiid:
            return AbstractVmwareVconf(disk)


if __name__ == '__main__':
   OdgNzdtUpgConf().main() 
```

Please assist with what the problem could be.


BR,
Kurt Arries

---

### Post by spjackson on 2016-08-05
At the basic level the error means that
```

vconf.getVmByType('db').getDiskByScsiId(3)

```
does not return a dictionary or array or similar which the caller expects. Here is some simple code that produces the same error.
```

#!/usr/bin/env python3

def myfunc():
    return None

print(myfunc()[0])

```
Presumaby getDiskByScsiId returns None when it cannot find what it is looking for. However, I cannot explain why it doesn't find what it is looking for.

---

