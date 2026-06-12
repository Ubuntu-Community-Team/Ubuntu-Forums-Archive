---
title: "[SOLVED] Importing I.E favorites into Firefox"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by sp00ner on 2008-07-05
I have my I.E. favorites folder copied to my NAS device. I am trying to get them imported into Firefox but cant seem to find an option for that. Is there a way?

---

### Post by steveneddy on 2008-07-05
Copy the bookmarks to the Desktop and tell FF to look there.

It's easier than trying to browse to the NAS, right?

---

### Post by sp00ner on 2008-07-05
I cant seem to even get a "Browse" dialog box to come up. I launch Firefox and select File > Import then I just get a window that says no programs that contain bookmarks can be found. No other options for pointing to a folder that contain bookmarks from other programs.

---

### Post by miwaypet on 2008-07-05
Go to bookmarks on main menu. Open it and select organize bookmarks. In new dialog box select import and backup. Easy steps from there.

---

### Post by sp00ner on 2008-07-05
OK I got it. What I needed to do was goto the Windows computer and export my favorites to an HTML file on the NAS and then point to that file in Firefox. My problem was, I was just trying to point to a folder that contained the actual shortcuts.

---

### Post by liuxianren on 2008-12-05
> **sp00ner said:**
> I have my I.E. favorites folder copied to my NAS device. I am trying to get them imported into Firefox but cant seem to find an option for that. Is there a way?

Hi,here is my python script deal with this issue. It transfer IE favorites folder with all it's subfolders and .url files into Firefox format Bookmarks file,which is a html file.

THis script is especially useful when you transfer from Windows to Linux(ubuntu), and just copy the IE favorites folder without export them to a html file, which can then be import to Firefox bookmarks.

I transfer from windows Vista to Ubuntu two weeks ago. One of the many problems is I couldn't use the Favorites collections of my IE. Firefox itself just give us an option to import the IE Favorites folder(bookmarks in FF) from the same operation system. This is my first python code and based on a piece of code from  [http://insom.me.uk/hacks/favs2html.html](http://insom.me.uk/hacks/favs2html.html). since I just learn it for one week,please ignore my coding skill. it's tested with Python2.5,python3.0 in both windowsXP and Ubuntu. I would be very happy if it useful for guys of my same situation.

the link:  [http://liuxianrenterry.spaces.live.com/blog/cns!5C780759565B7177!193.entry](http://liuxianrenterry.spaces.live.com/blog/cns!5C780759565B7177!193.entry)

---

### Post by liuxianren on 2008-12-05
[B]Hi,here is my python script deal with this issue. It transfer IE favorites folder with all it's subfolders and .url files into Firefox format Bookmarks file,which is a html file.

THis script is especially useful when you transfer from Windows to Linux(ubuntu), and just copy the IE favorites folder without export them to a html file, which can then be import to Firefox bookmarks.

I transfer from windows Vista to Ubuntu two weeks ago. One of the many problems is I couldn't use the Favorites collections of my IE. Firefox itself just give us an option to import the IE Favorites folder(bookmarks in FF) from the same operation system. This is my first python code and based on a piece of code from  [http://insom.me.uk/hacks/favs2html.html](http://insom.me.uk/hacks/favs2html.html). since I just learn it for one week,please ignore my coding skill. it's tested with Python2.5,python3.0 in both windowsXP and Ubuntu. I would be very happy if it useful for guys of my same situation.

the link:  [http://liuxianrenterry.spaces.live.com/blog/cns!5C780759565B7177!193.entry](http://liuxianrenterry.spaces.live.com/blog/cns!5C780759565B7177!193.entry)[/B]

Someone doesn't find my code.... So I post it here.The link above you can actually not only find the code,but also the screenshots and a test pack with a Favorites example folder inside.

**[COLOR="Red"]CODE:[/COLOR]**

```

#! /usr/bin/python
#coding:UTF-8

################################################################################
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
#
#
#############################################################################
#     This module is used to generate firefox Bookmarks format html file from Windows IE Favorites folder(.url files)
#by Liu Tao< liuxianren<ignorethis>@gmail.com>, http://liuxianren.id1314.com
#
#This module was based on  a work by Aaron Brady and Steve Clarke Steve Clarke <sclarke<at>frognet.net>
#found here   http://insom.me.uk/hacks/favs2html.html
# which distributed under GNU/GPL lisence.
#############################################################################


import ConfigParser
import os
import sys
import time
import tkFileDialog
import Tkinter
import tkMessageBox





class FavsProcessorBase:
    """Base class iterates through favorites and generates events.
    Create a descendent that overrides the event handlers to perform the
    desired transformation.

    """
    def __init__(self, rootdir):
        self.rootdir = rootdir
        self.level = 0
        self.recurse = 1

    def to_unicode(self,
         obj, encoding='UTF-8'):
        if isinstance(obj, basestring):
            if not isinstance(obj, unicode):
                obj = unicode(obj, encoding)
        return obj

    def generate(self, stream=sys.stdout):
        """Initiate the processing of the favorites from the root directory.

        """
        self.level = 0
        self.beforeFavorites(stream)
        self.doFolder(self.rootdir, stream)
        self.afterFavorites(stream)

    def doFolder(self, folder, stream):
        """Iterate through the items in the folder generating events for
        favorites contained by the folder. If recurse is 1 nested folders
        will be processed recursively.

        """
        self.beforeFolder(folder, stream)
        self.level += 1
        try:
            pathItems = os.listdir(folder)
            files =[]
            folders = [] 
            for filename in pathItems:
                try:
#                    sFilesystemencoding=sys.getfilesystemencoding()
#                    filename=filename.decode(sFilesystemencoding)
                    filename=self.to_unicode(filename)
                    
                    os.path.normpath(filename)
                    fd = os.path.join(folder, filename)
                    if os.path.isfile(fd) and filename[-4:].lower() == ".url":
                        files.append(fd)
                    elif os.path.isdir(fd):
                        folders.append(fd)
                    else:
                        # don't do anything with files that don't end with .url
                        pass
                except Exception, e:
                    print "doFolder.errer:",str(e)
                    #self.doFileError(filename, stream, str(e))

            if folders and self.recurse:
                folders.sort()
                for fd in folders:
                    print fd.encode("UTF-8")
                    self.doFolder(fd, stream)
            if files:
                files.sort()
                for fd in files:
                    print fd.encode("UTF-8")
                    self.doFavorite(fd, stream)
        finally:
            try:
                self.afterFolder(folder, stream)
            finally:
                self.level -= 1

    def beforeFavorites(self, stream):
        """Event generated before any favorites or folders are processed. Can
        be used to write out the start of a document.
        """
        pass

    def doFileError(self, file, stream, message=None):
        """Generated when any exception is thrown while iterating through the
        favorites.

        """
        print >>stream, "   "*self.level + "="*30
        print >>stream, "   "*self.level + "Unable to process item: %s" % file
        if not message is None:
            print >>stream, "   "*self.level + message
        print >>stream, "   "*self.level + "="*30

    def beforeFolder(self, folder, stream):
        """Event generated before any items contained in the folder are
        processed.

        """
        print "beforeFolder()"+ "   "*self.level+os.path.split(folder)[-1].encode("UTF-8")
        print >>stream, "   "*self.level+os.path.split(folder)[-1].encode("UTF-8")

    def doFavorite(self, file, stream):
        pathParts = os.path.split(file)
        print "doFavorite()"+"   "*self.level + pathParts[-1].encode("UTF-8")
        print >>stream, "   "*self.level + pathParts[-1].encode("UTF-8")

    def afterFolder(self, folder, stream):
        """Event generated after all items contained in the folder are
        processed.

        """
        pass

    def afterFavorites(self, stream):
        """Event generated after all items have been processed. Use to finish
        out the document.

        """
        pass


class FavstoHtml(FavsProcessorBase):
    """Generate html to provide links to the favorites sites.

    """
    def __init__(self, rootdir):
        FavsProcessorBase.__init__(self, rootdir)
        self.stream = None

    def indent(self, value, stream=None):
        if stream is None:
            stream = self.stream
        print >>stream, "&nbsp;"*3*self.level + str(value)

    def beforeFavorites(self, stream):
        print >>stream, """<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1>Bookmarks Menu</H1>
            """
        print >>stream, "<H1><I>Favorites files generated: %s</I></H1>" % time.ctime()

    def beforeFolder(self, folder, stream):
        print "html.beforeFolder()"+os.path.split(folder)[-1].encode("UTF-8")
        print >>stream, "<DT><H3>%s</H3><DL><p>"% os.path.split(folder)[-1].encode("UTF-8")


    def afterFolder(self, folder, stream):
        if self.level == 0: return
        print >>stream,"""</DL><p>"""


    def doFileError(self, file, stream, message=None):
        """Generated when any exception is thrown while iterating through the
        favorites.
        """
        pass

    def doFavorite(self, file, stream):
        foo = os.path.split(file)
        title = foo[-1][:-4]
        parser = ConfigParser.ConfigParser()
        parser.readfp(open(file))
        try:
            print >>stream, (
                "<DT><A HREF=\"%s\">%s</A>" % (
                    parser.get("InternetShortcut","URL").decode("utf-8").encode("UTF-8"),
                    title.encode("utf-8")
                    ))
        except Exception, e:
            print >>stream, "Exception: dofavorite!%s" % e

    def afterFavorites(self, stream):
        print >>stream, "<H1> all finished! You can now import this file to your FireFox browser as BookMarks!</H1>"


class App:
    favdir=None#u"/home/terry/Desktop/temp/Favorites"
    sFout=None
    frame=None#the main frame

    def __init__(self,root):
        self.frame=Tkinter.Frame(root,width=60,height=40)
        self.frame.grid()
        Tkinter.Label(self.frame, text="Browse your IE Favorites folder:\n(&#22914;&#26524;&#20320;&#29992;&#30340;&#26159;windows,"+\
            "&#35813;&#25991;&#20214;&#22312;C:\\Documents and Settings\\UERNAME\\Favorites").grid(row=0,column=0,columnspan=2)

        self.txtBrowse=Tkinter.Entry(self.frame,width=45,bg="white")
        self.txtBrowse.grid(row=1,column=0)
        btnBrowse=Tkinter.Button(self.frame,text="Browse...",command=self.digBrowse)
        btnBrowse.grid(row=1,column=1)

        Tkinter.Label(self.frame,text="please choose where to save your generated html file:").grid(row=2,column=0,columnspan=2)
        self.txtSave=Tkinter.Entry(self.frame,width=45,bg="white")
        self.txtSave.grid(row=3,column=0)
        btnSave=Tkinter.Button(self.frame,text="save to...",command=self.digSave)
        btnSave.grid(row=3,column=1)
        
        Tkinter.Label(self.frame,text="press to start convert:").grid(row=4,columnspan=2,column=0)
        btnStart=Tkinter.Button(self.frame,text="S T A R T",fg="red",width=20,command=self.funStart)
        btnStart.grid(row=5,column=0,columnspan=2,pady=12)
        btnStart.focus_set()

    def digBrowse(self):
        self.favdir=tkFileDialog.askdirectory(parent=root,initialdir=os.path.split(__file__)[0],\
            title="please choose the root folder of your IE Favorites")
        self.txtBrowse.delete(0,"end")
        self.txtBrowse.insert(0,self.favdir)
        #return favdir


    def digSave(self):
        self.sFout=tkFileDialog.asksaveasfilename(parent=self.frame,initialdir=os.path.split(__file__)[0],\
             filetypes=[('Firefox Bookmarks','*.html')] ,title="Save the generated bookmarks as...")
        self.txtSave.delete(0,"end")
        self.txtSave.insert(0,self.sFout)

    def funStart(self):
        if not (self.txtSave.get()=="" or self.txtBrowse.get()==""):
            self.sFout=self.txtSave.get()
            self.favdir=self.txtBrowse.get()
        if self.sFout==None or self.favdir==None:
            tkMessageBox.showerror("warning:", "you MUST choose both Favorites path and save to file!")
            return
        fout = open(self.sFout, 'w')
        try:
            gen = FavstoHtml(self.favdir)
            gen.stream = fout
            gen.generate(fout)
            tkMessageBox.showinfo("Finished!", "The convert from IE Favorites URLs to Firefox"+\
                "Bookmarks has been finished.you can find your generated BookMarks html file as %s"%app.sFout)
        finally:
            fout.close()



if __name__ == '__main__':
    root=Tkinter.Tk()
    root.title("IE Favorites to Firefox Bookmarks")
    app=App(root)
    root.mainloop()

```

DOWNLOAD here:[http://libz8a.bay.livefilestore.com/y1p4ROLvlK4Rc5cEUB2_Q5mMP_08HfxARxW4iV6lbULNbTJOwmwLclTcPO4skvVi0NIBXkSbTcq3vbemU_3ghDgMA/IE2FFbookmarks.zip?download](http://libz8a.bay.livefilestore.com/y1p4ROLvlK4Rc5cEUB2_Q5mMP_08HfxARxW4iV6lbULNbTJOwmwLclTcPO4skvVi0NIBXkSbTcq3vbemU_3ghDgMA/IE2FFbookmarks.zip?download)
or
[http://cid-5c780759565b7177.skydrive.live.com/self.aspx/Public/IE2FFbookmarks.zip](http://cid-5c780759565b7177.skydrive.live.com/self.aspx/Public/IE2FFbookmarks.zip)[/B]
LINK FIXED! 2009&#24180;10&#26376;09&#12288;liuxianren

---

### Post by philinux on 2008-12-05
Links dont show the code.

[edit] dont show your code.

---

### Post by liuxianren on 2008-12-06
You can also download the code without screenshot here:
[http://cid-5c780759565b7177.skydrive.live.com/self.aspx/Public/IE2FFbookmarks.zip](http://cid-5c780759565b7177.skydrive.live.com/self.aspx/Public/IE2FFbookmarks.zip)

the screenshots:
[http://liuxianrenterry.spaces.live.com/blog/cns!5C780759565B7177!193.entry]("http://liuxianrenterry.spaces.live.com/blog/cns!5C780759565B7177!193.entry")

---

### Post by philinux on 2008-12-06
Thanks very much, the screenshot was not displaying for me last night. Very weird.
Cheers

---

### Post by liuxianren on 2008-12-07
> **philinux said:**
> Thanks very much, the screenshot was not displaying for me last night. Very weird.
Cheers

You are welcome. 

That's maybe my first little contribution to open source world. I would be very glad if anyone can get something useful from my posts.:p

---

### Post by balleyne on 2010-09-07
Thanks very much, big help!

---

### Post by LucyDog on 2010-12-08
Perfect. This solved my problem. You give better info than I could find on the Firefox support site.

---

### Post by djdg on 2011-07-15
Too bad. I guess this comes too late for me. I directly saved the IE favourites without making a .html file. Have they now become useless?

---

### Post by gen2600 on 2012-04-17
> **liuxianren said:**
> You are welcome. 

That's maybe my first little contribution to open source world. I would be very glad if anyone can get something useful from my posts.:p

Dude, great job.  Totally came through in a crunch.

---

### Post by oldos2er on 2012-04-17
Closed, necromancy.

---

