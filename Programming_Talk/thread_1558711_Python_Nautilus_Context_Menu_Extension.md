---
title: "Python Nautilus Context Menu Extension"
date: 2010-08-22
forum: Programming Talk
---

### Post by MarekSkalicky on 2010-08-22
I'm trying to create NFS sharing script and add simple Menu Item into nautilus context menu, with python-nautilus.

But the script seems to don't run. I've placed it into
/usr/lib/nautilus/extensions-2.0/python/ with chmod 755.

```
import os,nautilus,sys,re
sys.path.append("/usr/local/etc/nfss")
import NFS

class NFSSMenuScript(nautilus.MenuProvider):
    def __init__(self):
        self.nfss=NFS.NFSShare()
    def get_file_items(self, window, files):
        if len(files) != 1:
                    return
        file=files[0]
        items=[]
        if file.is_directory():
            if self.check_mount(file):
                item = nautilus.MenuItem('NautilusPython::NFSShare_item_umount', 'Umount NFS' ,'Umount file %s' % file.get_name())
                item.connect("activate", self.menu_umount, file)
                items.append(item)
                return items
            elif self.check_share(file):
                item = nautilus.MenuItem('NautilusPython::NFSShare_item_mount', 'Mount NFS' ,'Mount file %s' % file.get_name())
                item.connect("activate", self.menu_mount, file)
                items.append(item)
                return items
            else:
                item = nautilus.MenuItem('NautilusPython::NFSShare_item_share', 'Share NFS' ,'Share file %s with NFS' % file.get_name())
                item.connect("activate", self.menu_share, file)
                items.append(item)
                return items
        else:
            return
    def menu_umount(self, menu, file):
        self.nfss.Umount(file.get_uri())
    def menu_mount(self, menu, file):
        self.nfss.Mount(file.get_uri())
    def menu_share(self, menu, file):
        self.nfss.Share(file.get_uri())
    def check_mount(self, file):
        path=file.get_uri()
        mount=self.nfss.network.GetMount()
        for x in mount:
            index=re.search(":/", x)
            string=x[(index.start()+1):]
            if path==string:
                return 1
        return 0
    def check_mount(self, file):
        path=file.get_uri()
        share=self.nfss.network.GetShare()
        for x in share:
            index=re.search(":/", x)
            string=x[(index.start()+1):]
            if path==string:
                return 1
        return 0

```Code of NFS.py (it is not copleted)
```
import os,re,shelve

class NFSShare():
    def __init__(self):
        self.database=Database()
        self.network=Network(self.database)
    
    def GetList(self):
        shares=[]
        base="/usr/local/etc/nfss/"
        adresy=open(base+"address.conf", "r")
        pocet=int(adresy.readline())
        seznam=[]
        for x in range(0,pocet):
            adr=adresy.readline()[:-1]
            path=base+"adr"+str(x)+"/"
            os.mkdir(path)
            if os.system("mount '"+adr+":"+base+"' '"+path+"'"):
                print "Chyba pripojeni: "+adr
                os.rmdir(path)
            else:
                soubor=open(path+"exports")
                for radek in soubor.readlines():
                    line=adr+":"+radek[:-1]
                    if (radek[0]!='#') and (adr+":/usr/local/etc/nfss" not in line):
                        index=re.search(r"\t| ", line)
                        shares.append(line[0:index.start()])
                soubor.close()
                os.system("umount -l '"+path+"'")
                os.rmdir(path)
        adresy.close()
        self.database.SetShare(shares)
    
    def SharedFolders(self):
        for x in self.database.GetShare():
            base=os.environ["HOME"]+"/.nfss/"
            name=self._GetName(x)
            os.mkdir(base+name)
            os.system("chmod 775 '"+base+name+"'")
    
    def _GetName(self, x):
        n1=os.path.basename(x)
        n2=x[:(re.search(":/", x).start())]
        name=n1+" ("+n2+")"
        return name
    
    def Test(self):
        self.GetList()
        self.SharedFolders()
        l=(self.database.GetShare()[0])
        self.network.Mount(l, self._GetName(l))
        a=raw_input("Kolik je hodin? ")
        print self.database.GetMount()
        self.network.Umount(l, self._GetName(l))
        print self.database.GetMount()
    
    def Mount(self, file):
        print "mount"
    def Umount(self, file):
        print "umount"
    def Share(self, file):
        print "share"

class Network():
    def __init__(self, database):
        self.base=os.environ['HOME']+"/.nfss/"
        self.database=database

    def Mount(self, path, name):
        if os.system("mount '"+path+"' '"+self.base+name+"'"):
            print "Chyba pripojeni: "+path
        else:
            self.database.AddMount(path)

    print "umount"
def Share(self, file):
    print "share"
    def Umount(self, path, name):
        if os.system("umount '"+self.base+name+"'"):
            print "Chyba odpojeni: "+name
        else:
            self.database.DelMount(path)


class Database():
    "Database NFS Share"
    def __init__(self):
        self.base=os.environ['HOME']+"/.nfss/"
        self.file=shelve.open(self.base+".shared")
    
    def GetShare(self):
        share=self.file["share"]
        return share
    
    def SetShare(self, list):
        self.file["share"]=list
    
    def GetMount(self):
        mount=self.file["mount"]
        return mount
    
    def AddMount(self, path):
        if self.file.has_key("mount"):
            mount=self.file["mount"]
            mount.append(path)
            self.file["mount"]=mount
        else:
            self.file["mount"]=[path]
    
    def DelMount(self, path):
        mount=self.file["mount"]
        index=mount.index(path)
        del mount[index]
        self.file["mount"]=mount
```What is wrong? 
Thanks Marek

---

