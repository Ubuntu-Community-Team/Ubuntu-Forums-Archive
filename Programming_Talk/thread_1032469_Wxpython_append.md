---
title: "Wxpython append"
date: 2009-01-06
forum: Programming Talk
---

### Post by irfan798 on 2009-01-06
the problem is if I give **app.MainLoop()** (at line 104), it just do "**for**" once but if i dont, it dont append progress (but it prints to console) until for thing finishes; 
So i want to reflesh "**control**" (at line 18 ) every loop but how can i do it?

[http://pastebin.ca/1301026]("http://pastebin.ca/1301026")

```


#!/usr/bin/python
# -*- coding: utf-8 -*-

import os
import os.path
import wx
import sys
import Image
ID_ABOUT=101
ID_EXIT=110
ID_OPEN=111
size = 128, 128
resim_sayisi=0
tamamlanan = 0
class MainWindow(wx.Frame):
    def __init__(self,parent,id,title):
        wx.Frame.__init__(self,parent,wx.ID_ANY, title, size = (200,100))
        self.control = wx.TextCtrl(self, 1, style=wx.TE_MULTILINE|wx.TE_READONLY)
        print self
        print self.control
        self.CreateStatusBar() # A StatusBar in the bottom of the window
        # Setting up the menu.
        filemenu= wx.Menu()
        filemenu.Append(ID_ABOUT, "&Hakk&#305;nda"," Bu program hak&#305;nda")
        filemenu.Append(ID_OPEN, "&Aç"," Bi&#351;ey açar")
        filemenu.AppendSeparator()
        filemenu.Append(ID_EXIT,"Ç&&#305;k&#305;&#351;"," Program&#305; kapat&#305;r")
        # Creating the menubar.
        menuBar = wx.MenuBar()
        menuBar.Append(filemenu,"&File") # Adding the "filemenu" to the MenuBar
        self.SetMenuBar(menuBar)  # Adding the MenuBar to the Frame content.
        wx.EVT_MENU(self, ID_ABOUT, self.OnAbout) # attach the menu-event ID_ABOUT to the
                                                           # method self.OnAbout
        wx.EVT_MENU(self, ID_EXIT, self.OnExit)   # attach the menu-event ID_EXIT to the
                                                           # method self.OnExit
		
        wx.EVT_MENU(self, ID_OPEN, self.OnOpen)												   
		
        self.Show(True)
    def OnAbout(self,e):
        d= wx.MessageDialog( self, " &#304;rfan Bilalo&#287;lu yazd&#305; bu program&#305; \n"
                            " wx pitonda","Program hakk&#305;nda", wx.OK)
                            # Create a message dialog box
        d.ShowModal() # Shows it
        d.Destroy() # finally destroy it when finished.
    def OnExit(self,e):
        self.Close(True)  # Close the frame.
	
    def OnOpen(self,e):
        """ Open a file"""
        self.dirname = ''
        dlg = wx.FileDialog(self, "Choose a file", self.dirname, "", "*.*", wx.OPEN)
        if dlg.ShowModal() == wx.ID_OK:
            self.filename=dlg.GetFilename()
            self.dirname=dlg.GetDirectory()
            print dlg.GetDirectory()
            print self
            f=open(os.path.join(self.dirname,self.filename),'r')
            self.control.AppendText("\n" + dlg.GetDirectory())
            f.close()
        dlg.Destroy()
        resim_kucult()



def resim_kucult():
	nere = "/home/irfan/Resimler/erdinç_antalya" + "/"
	
#duzelt beni ::: os.walk yerine sadece tek dizini gezssin
	for root, dirs, files in os.walk(nere):
	
#resimlerin sayisini bul
	
		for resim_sayi in files:
			son_ek = os.path.splitext(resim_sayi)[1]
			if son_ek == ".JPG" or son_ek == ".jpg" or son_ek == ".JPEG" or son_ek == ".jpeg" or son_ek == ".png":
				
				global resim_sayisi
				resim_sayisi += 1
		
		print resim_sayisi, "tane resim var"
		frame.control.AppendText("try")
	
		os.mkdir(root + "kucuk")

#root u kucuk olarak ayarla
		
		root_yeni=root + "kucuk/"
		
		for resim_tek in files:
			resim = root + resim_tek
			son_ek = os.path.splitext(resim_tek)[1]
			if son_ek == ".JPG" or son_ek == ".jpg" or son_ek == ".JPEG" or son_ek == ".jpeg" or son_ek == ".png":
				outfile = root_yeni + "k_" + os.path.splitext(resim_tek)[0] + ".jpg"
				if resim != outfile:
					try:
						im = Image.open(resim)
						im.thumbnail(size)
						im.save(outfile, "JPEG")
						global tamamlanan
						tamamlanan += 1
						print resim_tek, "resmi tamam     [", tamamlanan, "/", resim_sayisi, "]"
						frame.control.AppendText('[%s/%s] \n'%(tamamlanan,resim_sayisi))
						app.MainLoop()

					except IOError:
						print resim, "icin kucuk hali olusturulamadi"

		else:
			print resim_tek, " dosyasi bir resim deil"
		print "---------------"





app = wx.PySimpleApp()
frame = MainWindow(None, -1, "Sample editor")
app.MainLoop()




```

---

### Post by MaxVK on 2009-01-06
Try this:

```
if __name__ == "__main__":
    app = wx.PySimpleApp(0)
    app.MainLoop()
```

---

### Post by irfan798 on 2009-01-06
Same problem

---

### Post by MaxVK on 2009-01-07
Perhaps set a timer event and refresh in that?

---

