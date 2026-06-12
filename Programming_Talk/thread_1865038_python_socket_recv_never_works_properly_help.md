---
title: "python socket recv never works properly help"
date: 2011-10-19
forum: Programming Talk
---

### Post by mushy365 on 2011-10-19
I've been writing a server and a guit client to try and get file transfer and basically just network commucation working. But the recv command nerver works properly. Some times ill send("simple line") and the output from reclieve will be  "simple line" other times it will have a load of other info on the end of it 

for example i want to connect to my server and the server lists the songs available for download 

originally i looked throught he files and sent each file name with one send command
the used a loop to recv and print each send command expecting  one filename per line 
instead i got 1024 bit blocks of text with leftover bits of earlier filenames despite not sending them in that send command. 

so i messed around with it for hours and hours and still cant get it working. Sometimes here is an example of the functions i have and the outputs from my debugging

**serv.py**
```

if(commands[0] == 'list'):
             whatpacketshouldlooklike=""
             print "[Request] List files ", address
             fil = list_files(path)
             for f in fil:
                sdata =  f  
                whatpacketshouldlooklike += sdata + "-EOS-"
                newSock.send(sdata +"-EOS-")
                #print "sent: " + sdata
             newSock.send("\r\n\r\nEOF")
             whatpacketshouldlooklike += "\r\n\r\nEOF"
             print "---------------------------------"
             print whatpacketshouldlooklike
             print "---------------------------------"

```

**cli.py**
```
def get_data(self,size = 1024):

        self.alldata = ""
        while 1:

          while gtk.events_pending():
             gtk.main_iteration()

          self.recvdata = self.s.recv(size)
          self.alldata += self.recvdata
          if self.alldata.find("\r\n\r\nEOF"):
             print "recieved end message"
             self.rdata = self.alldata[:self.alldata.find("\r\n\r\nEOF")]
             break

          
        
        print "All data Recieved: " + str(len(self.rdata)) + "Bytes"
        print "All data :\n" + self.rdata + "\n-------------------------------------------------"  

        self.infiles = self.rdata.split("-EOS-")
        for nf in self.infiles:
           if len(nf) > 2:
              self.add_message(self.incomingIcon,nf)
```

The two problems with this code. sometimes it works properly and lists all the files, sometimes it lists one file. 

The second problem is once i press the button to send one command, if it works and i get the proper response,  when i type a new command and press the button again 100% of the time the gui application freezes.  I dont know why. full codes

```
#!/usr/bin/python
import os, glob, shutil
import sys
import socket
import time
import string
import ConfigParser

#functions
def sendfile(socket,path,name):
    confirm = socket.recv(1024)
    if(confirm == "_BEGIN_"):
      #get file size
      siz = os.path.getsize(path + name)
      socket.send("_F_SIZ_=" + str(siz))
      
      fullfile = path + name
      print "[Notice] sending file " + fullfile
      if os.path.exists(fullfile):
         #file exists we can transfer it.
         #open file in rb
         #loop through and send to socket
         f = file(fullfile,'rb')
         
         while True:
            data = f.read(1024)
            if len(data) <= 0:
               socket.send(data)
               break
            socket.send(data)
         
         f.close()
         print "[Notice] finished sending file " + fullfile

    else:
      print "No confirmation recieved"

def list_files(path):
   os.chdir(path)
   ffiles = glob.glob("*.*")  
   return ffiles; 


def usage():
   print "usage: filerec.py [portnumber][base address to read from]"

#usage: filerec.py [portnumber][base address to read from]
#check argv 

if(len(sys.argv) > 2):
   #we have at least 3 args we can contunue
   port = int(sys.argv[1])
   path = sys.argv[2]
   
   if os.path.isdir(path):
      #path is valid
      print "Server listening - Serving files from " + path
      # now lets create a socket
      sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
      sock.bind(('', port))
      sock.listen(5)

      #loop to accept connections.
      
      while True:
         sdata = ""
         newSock, address = sock.accept()
         print "**Connection from ", address
      
         rcvdata = newSock.recv(1024)
         commands = rcvdata.split(' ')


         if(commands[0] == 'list'):
             whatpacketshouldlooklike=""
             print "[Request] List files ", address
             fil = list_files(path)
             for f in fil:
                sdata =  f  
                whatpacketshouldlooklike += sdata + "-EOS-"
                newSock.send(sdata +"-EOS-")
                #print "sent: " + sdata
             newSock.send("\r\n\r\nEOF")
             whatpacketshouldlooklike += "\r\n\r\nEOF"
             print "---------------------------------"
             print whatpacketshouldlooklike
             print "---------------------------------"


         elif(commands[0] == 'get'):
             #remove first word
             filenam = " ".join(commands[1:])
             print "**Requested download of " + filenam
             if(os.path.exists(path + filenam)):
                newSock.send("_YESFILE_")
                sendfile(newSock,path,filenam)
                
             else:
                print "File does not exist" + path + filenam
                newSock.send("_NOFILE_")
         elif(commands[0] == 'quit'):
             newSock.close()
             sock.close()
             print "**Remote host terminated connection"
             break;
         
         else:
            print "**Invalid command " + rcvdata
            newSock.send("Invalid command \r\n\r\nEOF")

   else:
      print "Invalid path " + path
      exit()
        


else:
   usage()
```



```
#!/usr/bin/env python

#imports
import os
import sys
import gtk
import glob
import string
import pygtk
import socket
import shutil
pygtk.require('2.0')


class Base:
    stopListening = False

    def sendcommand(self,widget):
        command = self.commandbartxtbox.get_text()
        if command.lower() == "quit":
           self.stopListening = True
           self.s.close()
           self.add_message(self.errorIcon, "Closed connection to server")

        elif command.lower() == "list":
           self.send_data(command)
           self.get_data(1024)
        else:
            self.send_data(command)
            self.get_data(1024)
           

    def send_data(self, data):
        #try to put the size 
        try:
          self.s.send(data)
          self.add_message(self.outgoingIcon,data)
        except:
          self.add_message(self.errorIcon,"Message Could not be sent")



    def get_data(self,size = 1024):

        self.alldata = ""
        while 1:

          while gtk.events_pending():
             gtk.main_iteration()

          self.recvdata = self.s.recv(size)
          self.alldata += self.recvdata
          if self.alldata.find("\r\n\r\nEOF"):
             print "recieved end message"
             self.rdata = self.alldata[:self.alldata.find("\r\n\r\nEOF")]
             break

          
        
        print "All data Recieved: " + str(len(self.rdata)) + "Bytes"
        print "All data :\n" + self.rdata + "\n-------------------------------------------------"  

        self.infiles = self.rdata.split("-EOS-")
        for nf in self.infiles:
           if len(nf) > 2:
              self.add_message(self.incomingIcon,nf)


          
       
        #self.add_message(self.errorIcon,"Error reading from host.")

    def treeview_changed(self,widget,event,data=None):
        adj = self.contentwindow.get_vadjustment()
        adj.set_value(adj.upper - adj.page_size)
       
    def add_message(self,pix,txt): 
        self.liststore.append([pix,txt])  

    def connect_to_host(self,widget):
        self.ip = self.connectbariptxtbox.get_text()
        self.port = self.connectbarporttxtbox.get_text()

        
        try:
          self.s.connect((self.ip, int(self.port))) 
          self.add_message(self.successIcon,"Successfully connected to host")
          
          
        except:
          self.add_message(self.errorIcon,"Error connection to host: " + self.ip + " on port" + self.port )
    
    def destroy(self,widget,data=None):
        gtk.main_quit()

    def set_images(self):
        self.currentdir = os.getcwd() + "/icons/"
        
        self.incomingIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "recv.png",24,24)
        self.outgoingIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "sent.png",24,24)
        self.errorIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "Error.png",24,24)
        self.successIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "success.png",24,24)

    def __init__(self):
        #lets get a window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.window.set_size_request(800,800)
        self.window.set_title("Remote File Downloader")

        #connectbar hbox
        #label ip txtbox label port  button connect
        self.connectbar = gtk.HBox()
        self.connectbar.set_size_request(800,30)
        
        #declare the connectbar widgets
        self.connectbariplabel = gtk.Label(" IP:")
        self.connectbariptxtbox = gtk.Entry()
        self.connectbariptxtbox.set_text("brian-movie-downloads")
        self.connectbariptxtbox.set_size_request(500,30)
        self.connectbarportlabel = gtk.Label("Port:")
        self.connectbarporttxtbox = gtk.Entry()
        self.connectbarporttxtbox.set_size_request(60,30)
        self.connectbarconnectbutton = gtk.Button("Connect")
        self.connectbarconnectbutton.connect("clicked",self.connect_to_host)

        #pack them into the bar
        self.connectbar.pack_start(self.connectbariplabel,False,False,5)
        self.connectbar.pack_start(self.connectbariptxtbox,False,False,5)
        self.connectbar.pack_start(self.connectbarportlabel,False,False,5)
        self.connectbar.pack_start(self.connectbarporttxtbox,False,False,5)
        self.connectbar.pack_start(self.connectbarconnectbutton,False,False,5)

        #scroll window hbar treeview and listview need to be declared before this
        self.contenthbar = gtk.HBox() 
        self.contenthbar.set_size_request(800,700)      
        #liststore creation
        self.liststore = gtk.ListStore(gtk.gdk.Pixbuf,str)
        #treeview
        self.treeview = gtk.TreeView(self.liststore)
        self.treeview.connect('size-allocate', self.treeview_changed)

        #self.treeview.connect("row-activated", self.on_src_activated)
        #self.treeview.set_rules_hint(True)

        #columns and cell rendering
        self.imgrend = gtk.CellRendererPixbuf()
        self.txtrend = gtk.CellRendererText()

        #columns
        self.imgcolumn = gtk.TreeViewColumn(" Action ", self.imgrend, pixbuf = 0)
        self.imgcolumn.set_min_width(70)

        self.txtcolumn = gtk.TreeViewColumn(" Data", self.txtrend, text = 1)
        self.txtcolumn.set_min_width(650)

        ##add columns
        self.treeview.append_column(self.imgcolumn)
        self.treeview.append_column(self.txtcolumn)


        
        self.contentwindow = gtk.ScrolledWindow()
        self.contentwindow.set_shadow_type(gtk.SHADOW_ETCHED_IN)
        self.contentwindow.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.contentwindow.add(self.treeview)
        
        self.contenthbar.pack_start(self.contentwindow)

        #delcare the command hbox
        self.commandbar = gtk.HBox()
        self.commandbar.set_size_request(800,30)

        #declare the commandbar txtbox and button
        self.commandbarsendbutton = gtk.Button("Send")
        self.commandbarsendbutton.connect("clicked",self.sendcommand)
        self.commandbartxtbox = gtk.Entry()
        self.commandbartxtbox.set_size_request(500,30)

        self.commandbar.pack_start(self.commandbartxtbox,False,False,5)
        self.commandbar.pack_start(self.commandbarsendbutton,False,False,5)

        #declare the vertical bar
        self.mainbar = gtk.VBox()
        self.mainbar.pack_start(self.connectbar,False,False,5)
        self.mainbar.pack_start(self.contenthbar,False,False,0)
        self.mainbar.pack_start(self.commandbar,False,False,5)
        
        #other functions to run before displaying window
        self.set_images()
        self.s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
  
        #self.add_message(self.successIcon,"Its working! Huzzah!!")
        #add to windown and display
        self.window.add(self.mainbar)
        self.window.show_all()
        self.window.connect("destroy",self.destroy)

        

    def main(self):
        gtk.main()





if __name__ == "__main__":
    base = Base()
    base.main()
```



please help, ive been working on this for ages. If someone could run the code on their machine and send me back the editing code, i feel like ive tried every solution i could google and non work for me. 

i just want this to happen 

enter ip and port and press connect 

it connects to ip and port  (that works fine)

then when you type in a command and press send 

i.e list - it gets a list of all files in remote drive and prints them each in a new row

then it doesnt grey out when you go to send a second command

---

### Post by 11jmb on 2011-10-19
I have a couple questions:

1. you said that there are multiple possible outcomes, are they repeatable? (if you run your client program twice and request the list multiple times each run, will the 1st, 2nd, etc. request have the same outcome?)

2. Can you try writing a simpler command first, like "hello" where the server will just respond with a simple message? It is often easier to figure out your mistakes on simpler problems before diving into the more complex routine

I am not going to go through everything and look for errors right away, because that wouldn't teach you anything. I would rather guide you through.

---

### Post by 11jmb on 2011-10-19
actually, ignore #1 for now, I misread your problem about sending multiple commands, but do the different outcomes arise from running the same code?

---

### Post by Arndt on 2011-10-20
I don't know about the rest, but does this test do what you intend?

```
         if self.alldata.find("\r\n\r\nEOF"):

```

When the string is not found, 'find' will return -1, which tests as True.

---

