---
title: "piklab and picc18"
date: 2008-03-02
forum: Programming Talk
---

### Post by Amazona aestiva on 2008-03-02
I've compiled the latest PikLab successfully, but I when I give it the path of the picc18 compiler it can't recognise it. It runs under wine.(Tested with MPLAB) 

Piklab wants an exe called picc18, but there is only mcc18.exe???

So I created a link to mcc with named picc, and still not recognised?!

Can anyone help me?

PS: In Piklab I can choose Unix/Windows c18 compiler, If there is a linux version, where would I find it?

---

### Post by Amazona aestiva on 2008-03-07
Please! Anyone!

This would be a great help to me!

---

### Post by gmagno on 2008-04-04
Hi,

I'm having a similar problem, i want to use Linux in my PIC projects, and, so far, i've been using pic-lite from hi-tech which has some limitations... But now i need to work with a PIC18f458 and can't find a compiler for this.

By the way, i need a bootloader too, i've tryed to use Python interface for the Tiny Pic Bootloader  ([COLOR="Blue"]http://trac.cihologramas.com/pytbl[/COLOR]) but with no success, because i'm using a laptop and have no serial port (RS232) - i use a USB to RS232 converter (which works fine with other applications), but in this case this python application only permits connection to /dev/ttySx and no /dev/ttyUSBx... If anyone could look at the code a tell me what to change, that would be great (i've already tryed it...).

Thanks in advance

---

### Post by gmagno on 2008-04-04
Let me make people's life easyer, here is the code:

```

#!/usr/bin/python

# pytbl.py Program to upload .hex file to a PIC microcontroler
# having the TinyPic Boot Loader.
#
# Copyright (C)2005 Combustion Ingenieros Ltda
#                   http://www.cihologramas.com
# Author: Ricardo Amezquita Orozco
#         <ramezquitao@cihologramas.com>
# 
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
# MA  02110-1301, USA.

# The TinyPic Boot Loader can be found at:
# http://www.etc.ugal.ro/cchiculita/software/picbootloader.htm

# The most recent version of this software, can be found at
# http://www.cihologramas.com/contrib/pytbl.html      
#

import os
from sys import exit
#Tratar de cargar wxPython para interfaz grafica,
#si no existe trabajar por consola
from time import sleep 
ID_ABOUT = 101
ID_EXIT  = 102
ID_DETECTPIC = 103
ID_TRANSFERFILE = 104
ID_BUSCARHEX= 105
ID_VEL=106
ID_PORT=107
ID_RTS=108


#Flag that indicates if the pic should be reseted using the RTS pin
RESET_RTS=False

try:
    GUI=True
    from wxPython.wx import *

    class MyFrame(wxFrame):
        def __init__(self, parent, ID, title):
            #Llamando el constructor de la clase superior
            wxFrame.__init__(self, parent, ID, title,
                             wxDefaultPosition, wxSize(-1, -1))

            self.CreateStatusBar()
            self.SetStatusText("PicTiny Bootloader")


            menu = wxMenu()
            menu.Append(ID_ABOUT, "&About",
                        "")
            menu.AppendSeparator()
            menu.Append(ID_EXIT, "E&xit", "Terminate the program")

            menuBar = wxMenuBar()
            menuBar.Append(menu, "&Help");

            self.SetMenuBar(menuBar)


            # Creando un dato de nombre control, para la clase MyFrame

            self.sizer=wxBoxSizer(wxVERTICAL)

            self.sizer.Add(wxStaticText(self, -1, "File to upload:",wxPoint(20, 30)),0,wxEXPAND)
            self.sizer2=wxBoxSizer(wxHORIZONTAL)
            self.hex_file = wxTextCtrl(self,1)
            self.search_hex_file=wxButton(self, ID_BUSCARHEX, "Find:")
            self.sizer2.Add(self.hex_file,3,wxEXPAND)
            self.sizer2.Add(self.search_hex_file,0,wxEXPAND)
            self.sizer.Add(self.sizer2,0,wxEXPAND)

            self.sizer4=wxBoxSizer(wxHORIZONTAL)

            self.sizer.Add(self.sizer4,10,wxEXPAND)

            self.sizer3=wxBoxSizer(wxVERTICAL)

            self.sizer4.Add(self.sizer3,0,wxEXPAND)




            self.detect_pic=wxButton(self, ID_DETECTPIC, "Detect Pic:")
            self.transfer_file=wxButton(self, ID_TRANSFERFILE, "Upload File:")

            self.sizer3.Add(self.detect_pic,0,wxEXPAND)
            self.sizer3.Add(self.transfer_file,0,wxEXPAND)
            self.sizer3.Add(wxStaticText(self, -1, "Port:",wxPoint(20, 30)),0,wxEXPAND)
            self.puertos=wxChoice(self,ID_PORT,choices=seriales)
            self.sizer3.Add(self.puertos,0,wxEXPAND)
            self.sizer3.Add(wxStaticText(self, -1, "Speed:",wxPoint(20, 30)),0,wxEXPAND)

            vels= ["300","1200","2400","4800","9600","19200","38400","57600","115200","230400"]

            self.velocidades=wxChoice(self,ID_VEL,choices=vels)
            self.sizer3.Add(self.velocidades,0,wxEXPAND)

            #self.sizer3.Add(wxStaticText(self, -1, "Reset PIC using RTS:",wxPoint(20, 30)),0,wxEXPAND)
            
            EVT_CHOICE(self,ID_VEL, self.set_vel)
            EVT_CHOICE(self,ID_PORT, self.set_port)

            self.ResetRTS=wxCheckBox(self,ID_RTS,"Reset PIC using RTS")
            self.sizer3.Add(self.ResetRTS,0,wxEXPAND)
            EVT_CHECKBOX(self,ID_RTS,self.set_rts)
            self.terminal = wxTextCtrl(self,1,style=wxTE_MULTILINE|wxTE_READONLY,size=wxSize(400,250))
            self.sizer4.Add(self.terminal,10,wxEXPAND)
            self.SetSizer(self.sizer)
            self.SetAutoLayout(1)
            self.sizer.Fit(self)
            self.Show(1)

            EVT_MENU(self, ID_ABOUT, self.OnAbout)
            EVT_MENU(self, ID_EXIT,  self.TimeToQuit)
            EVT_BUTTON(self,ID_TRANSFERFILE,self.TransferFile)
            EVT_BUTTON(self,ID_BUSCARHEX,self.bu_hex)
            EVT_BUTTON(self,ID_DETECTPIC,self.DetectPic)

        def TransferFile(self,event):
            TransferFile(self,self.hex_file.GetValue())


        def DetectPic(self,event):
            DetectPic(self)


        def set_vel(self,event):
            global BAUDRATE
            BAUDRATE=int(self.velocidades.GetString(self.velocidades.GetSelection()))
            print BAUDRATE

        def set_port(self,event):
            global PORT
            if self.puertos.GetCount()==0:
                PORT=-1
                twrite(self,"No available serial ports\n")
                self.detect_pic.Enable(FALSE)
                self.transfer_file.Enable(FALSE)
            else:
                PORT=self.puertos.GetString(self.puertos.GetSelection()) 
                #try:
                #    PORT=int(self.puertos.GetString(self.puertos.GetSelection())) 
                #except:
                #    PORT=0
            if PORT=="": PORT=self.puertos.GetString(0)
            #Verificar si se detecto por string o por numero
            if PORT!=-1:
                if len(PORT)==1: PORT=int(PORT)
            print "Ojo: configurado el puerto",PORT

        def set_rts(self,event):
            global RESET_RTS
            RESET_RTS=self.ResetRTS.GetValue()
        def OnAbout(self, event):
            dlg = wxMessageDialog(self,
                                  "Program to upload Intel hex files\n"
                                  "to PIC microcontrolers having the\n"
                                  "Tiny PIC bootloader.",
                            "About PyTyBld", wxOK | wxICON_INFORMATION)
            dlg.ShowModal()
            dlg.Destroy()


        def TimeToQuit(self, event):
            self.Close(true)


        def bu_hex(self, event):
            dirname=os.getcwd()
            dlg = wxFileDialog(self, "Select File:", dirname, "",
                               "Hex files (*.hex)|*.hex|Any (*.*)|*.*", wxOPEN) 
            if dlg.ShowModal() == wxID_OK: 
                self.hex_file.SetValue(os.path.join(dlg.GetDirectory(),dlg.GetFilename())) 
            dlg.Destroy()




    class MyApp(wxApp):
        def OnInit(self):
            frame= MyFrame(NULL, -1, "Tiny Boot Loader")
            frame.Show(true)

            self.SetTopWindow(frame)

            #Configurar el serial de acuerdo a la interfaz grafica
            frame.velocidades.SetSelection(8)

            twrite(frame,"This program is distributed in the hope that it"
                   " will be useful, but WITHOUT ANY WARRANTY; without "
                   "even the implied warranty of MERCHANTABILITY or FITNESS"
                   " FOR A PARTICULAR PURPOSE. See the GNU General Public "
                   "License for more details. "
                   "http://www.gnu.org/copyleft/gpl.html \n\n"
                   "Report any bugs, critics, and suggestions to \n"
                   "ramezquitao@cihologramas.com\n\n") 
            frame.set_vel(None)
            frame.set_port(None)
            
            return true

    WXP=True
except ImportError:
    GUI=False
    WXP=False

try:
    import serial
    #Configuracion por defecto del puerto
    #PORT=0
    #BAUDRATE=115200
except ImportError:
    exit("\n\nRequired module serial (Python-Serial) not found\n")




#Verificar que seriales hay disponibles
def check_serial():
    seriales=[];
    for i in range(0,8):
        try:
            ser=serial.Serial(port=i)
            #ser.open()
            ser.close()
            seriales.append(str(i))
        except serial.SerialException:
            continue
    #verificar puertos USB
    for i in ("/dev/ttyUSB0","/dev/ttyUSB1","/dev/ttyUSB2"):
        try:
            ser=serial.Serial(port=i)
            #ser.open()
            ser.close()
            seriales.append(str(i))
        except serial.SerialException:
            continue
    
    return seriales


          
def DetectPic(gui):
    try:
        s=serial.Serial(PORT,BAUDRATE,timeout=1)
        
    except serial.serialutil.SerialException:
        if gui !=None:
            twrite(gui,"Could not open serial port "+str(PORT))
            return None,None
        else:
            parser.error("Could not open serial port "+str(PORT))
        
    except ValueError:
        if gui !=None:
            twrite(gui,"Invalid baud rate: "+str(BAUDRATE))
            return None,None
        else:
            parser.error("Invalid baud rate "+str(BAUDRATE))
    #s.open()
    #Borrar cualquier informacion que haya podido estar entrando por el serial
    s.flushInput()

    #Resetear el microcontrolador
    if RESET_RTS:
        s.setRTS(1)
        sleep(.1)
        s.setRTS(0)
        sleep(.1)

    
    #Solicitar al microcontrolador su ID
    s.write(chr(0xC1))
    ret=s.read(2)
    if len(ret)!=2:
        twrite(gui,"Error, PIC not available\n")
        s.close()
        return None,None
    #Leer el tipo de pic retornado por la tarjeta
    if ret[1]!= "K":
        twrite(gui,"Error, PIC not recognized (protocol error)\n")
        s.close()
        return None,None
        
    pt=ord(ret[0])
    
    s.flushInput()
    s.close()

    if pt==0x31:
        PicType="16F876A-16F877A";
        max_flash=0x2000;
    elif pt==0x32:
        PicType="16f873A-p16f874A";
        max_flash=0x1000;
    elif pt==0x33:
        PicType="16F87-16F88";
        max_flash=0x1000;
    elif pt==0x41:
        PicType="18F252-18F452";
        max_flash=0x8000;
    elif pt==0x42:
        PicType="18F242-18F442";
        max_flash=0x4000;
    elif pt==0x43:
        PicType="18F258-18F458";
        max_flash=0x8000;
    elif pt==0x44:
        PicType="18F248-18F448";
        max_flash=0x4000;
    elif pt==0x45:
        PicType="18F1320-18F2320";
        max_flash=0x2000;
    elif pt==0x46:
        PicType="18F1220-18F2220";
        max_flash=0x1000;
    elif pt==0x47:
        PicType="18F4320";
        max_flash=0x2000;
    elif pt==0x48:
        PicType="18F4220";
        max_flash=0x1000;
    elif pt==0x4A:
        PicType="18F6720-18F8720";
        max_flash=0x20000;
    elif pt == 0x4B:
        PicType="18F6620-18F8620"
        max_flash=0x10000
    elif pt ==0x4C:
        PicType="18F6520-18F8520"
        max_flash=0x8000
    elif pt==0x4D:
        PicType="18F8680";
        max_flash=0x10000;
    elif pt==0x4E:
        PicType="18F2525-18F4525";
        max_flash=0xC000;
    elif pt==0x4F:
        PicType="18F2620-18F4620";
        max_flash=0x10000;
    elif pt==0x55:
        PicType="18F2550-18F4550";
        max_flash=0x8000;
    elif pt==0x56:
        PicType="18F2455-18F4455";
        max_flash=0x6000;
    else:
        PicType="Microcontroller not supported or not detected";
        max_flash=None;

    family=None

    if (pt==0x31) or (pt==0x32):
        family="16F8XX"
    elif (pt==0x33):
        family="16F8X"
    elif (pt>0x40) and (pt<0x60):
        family="18F"
        
    twrite(gui,"Detected Microcontroller:\n"+PicType+"\n\n") 
    s.close()
    return max_flash,family

    



def TransferFile(gui,filename):
    # Diccionario utilizado para guardar la info del .hex
    # se utilizara para poder enviar al pic la info de 4 en 4 words (8 bytes)
    # para cumplir con los requerimientos de grabacion 

    # Dictionary used to store the data of the .hex file
    # it will be used to be able to send the info to the pic in the
    # block sizes required by the tinypic Bootloader

    # should be renamed to hex_mem, because it correspond to the hex file
    # data
    pic_mem={}
        
    max_flash,family=DetectPic(gui)

    if max_flash==None:
        return None
    try:
        f=open(filename, 'r')
    except IOError:
        twrite(gui,"Can't open file:"+filename+"\n\n")
        return None
    hexfile=f.readlines()
    f.close()
    le=len(hexfile)
    act=0;
    twrite(gui,"Uploading file: "+filename+"\n\n")
    for rec in hexfile:
        act=act+1
        # This is not working rigth the percent it is not shown
        if GUI:
            gui.SetStatusText("Finished "
                               +str(100.*float(act)/float(le))+"%")
            
        # Check for the record begining
        if rec[0]!=":":
            twrite(gui,"Hex file not recognized:\nLine: "+str(act)+
                   " File: "+filename+"\n\n")
            f.close()
            return None
        # Read the register size
        rl=eval("0x"+rec[1:3])
            
        # Read the register address 
        # Have in mind that the phisical PIC address is half of the
        # address registered in the .hex file for the 16F familly

        di=eval("0x"+rec[3:7])
            
        # Read the register type

        rt=eval("0x"+rec[7:9])

        # Calculate checksum
        chs=rl+eval("0x"+rec[3:5])+eval("0x"+rec[5:7])+rt
        # Only use the data register
        if rt==0:
            for i in range(9,9+2*rl,2):
                data=rec[i:i+2]
                
                # Calculate hex file checksum
                chs=chs+eval("0x"+data)

                # store data in pic_mem (it uses hex file address)
                # and move the first 4 address to the needed location
                
                if di < 0x08:
                    if family=="16F8XX" or family=="16F8X":
                        pic_mem[di+2*max_flash-200]=eval("0x"+data)
                    elif family=="18F":
                        pic_mem[di+max_flash-200]=eval("0x"+data)
                else:
                    pic_mem[di]=eval("0x"+data)

                di=di+1

                #Calculate hex file checksum
                chs=((-chs)&255)
                # TODO: Check the hex file checksum
                
    # The programing block size is family dependant:
    # For the 16F8XX family the block size is 8 bytes long (check in the
    # asm file for the max block size) 
    # For the 18F family the block size is 64 byte long



    if family=="16F8XX":
        hblock=8 #Hex Block 8 bytes
        block=4  #PIC Block 4 instructions (8 memory positions)
        maxpos=max_flash-100+4
        minpos=4
        
        
    if family=="16F8X":
        #The pic 16F87 and 16F88 do erase the program memory in blocks
        #of 32 word blocks (64 bytes)
        
        hblock=64 #Hex Block 64 bytes
        block=32  #PIC Block 32 instructions (64 memory positions)
        
        maxpos=max_flash-100+4
        minpos=0
        
        pic_mem[0]=0x8A
        pic_mem[1]=0x15
        pic_mem[2]=0xA0
        pic_mem[3]=0x2F
        
    
        
    if family=="18F":
        # The blocks have to be written using a 64 bytes boundary
        # so the first 8 bytes (reserved by TinyPic) will be re writen
        # So we have to include a goto max_flash-200+8


        goto_add=((max_flash-200+8)/2)
        hh_goto=(goto_add/0x10000)&0x0F
        h_goto=(goto_add/0x100)&0xFF
        l_goto=goto_add&0xFF
        
        pic_mem[0]=l_goto
        pic_mem[1]=0xEF
        pic_mem[2]=h_goto
        pic_mem[3]=0xF0+hh_goto
        block=64
        hblock=64
        maxpos=max_flash-200+8
        minpos=0

    for pic_pos in range(minpos,maxpos,block):
        
        mem_block=[255]*hblock
        write_block=False
        for j in range(0,hblock):

            #Remember .hex file address is pic_address/2 for the 16F familly
            if (family=="16F8XX") or (family == "16F8X"):
                hex_pos=2*pic_pos+j
            elif family=="18F":
                hex_pos=pic_pos+j
            else :
                twrite(gui,"Error, family not suported:",family)
                return
            
            if pic_mem.has_key(hex_pos):
                mem_block[j]=pic_mem[hex_pos]
                write_block=True
                
        if write_block:
            ret=write_mem(gui,pic_pos,mem_block,family)
            if ret!="K":
                return 
    twrite(gui,"Ready!!\n\n")
                
                
                
def write_mem(gui,pic_pos,mem_block,family):


    s=serial.Serial(PORT,BAUDRATE,timeout=1)
    #Resetear el microcontrolador
    #Es necesario pues el py serial mueve la pata RTS cuando se configura
    #El puerto
    if RESET_RTS:
        s.setRTS(1)
        sleep(.1)
        s.setRTS(0)
        sleep(.1)
        #Solicitar al microcontrolador su ID
        s.write(chr(0xC1))
        ret=s.read(2)

    s.flushInput()
        
    hm=(pic_pos/256)&255
    lm=(pic_pos&255)
    rl=len(mem_block)

    if (family=="16F8XX")or(family=="16F8X"):
        # Calculate checksum
        chs=hm+lm+rl
        s.write(chr(hm)+chr(lm)+chr(rl))
        for i in range(0,rl):
        
            # Calculate checksum
            chs=chs+mem_block[i]
            
            s.write(chr(mem_block[i]))
            
        chs=((-chs)&255)
        s.write(chr(chs))




    if family=="18F":
        # Calculate checksum
        chs=hm+lm+rl
        # the pic receives 3 byte memory address
        # U TBLPTRH TBLPTRL
        # Todo: Check if U can be different to 0
        #           U TBLPTRH TBLPTRL
        s.write(chr(0)+chr(hm)+chr(lm)+chr(rl))
        for i in range(0,rl):
            # Calculate checksum
            chs=chs+mem_block[i]
            
            s.write(chr(mem_block[i]))
    
        chs=((-chs)&255)
        s.write(chr(chs))

    ret=s.read(1)
    #ret="K"
    s.close()
    if ret!="K":
        twrite(gui,"Error writing to the memory position: "+
                    hex(pic_pos)+"\n\n")
    return ret
        
    


def twrite(gui,data):
    if gui:
        gui.terminal.SetInsertionPointEnd()
        gui.terminal.WriteText(data)
    else:
        print data


if __name__ == '__main__':
    seriales=check_serial()
    from optparse import OptionParser
    parser=OptionParser(description="Program to upload Intel hex files"
                        " to PIC microcontrolers having the Tiny PIC"
                        " bootloader. "
                        "To use a wxWidgets GUI, invoke it with no options."
                        " The most recent version of this software, can be"
                        " found at: "
                        "http://www.cihologramas.com/contrib/pytbl.html . "
                        "The Tiny Pic bootloader, can be found at: "
                        "http://www.etc.ugal.ro/cchiculita/software/picbootloader.htm. Report bugs to <ramezquitao@cihologramas.com>"
                        ,version="%prog 0.1",
                        usage="%prog [options] [-f FILENAME [-p PORT] [-b BAUDRATE]]")

    parser.add_option("-f","--file",action="store", type="string",
                      dest="filename",
                      help="Intel Hex formated file to be bootloaded. It is a "
                      "required parameter when PORT or BAUDRATE are given.")
    parser.add_option("-p","--port",action="store", type="int", dest="port",
                      help="Integer number used to specify the serial port"
                      " to be used. Ports are enumerated from 0."
                      " Default PORT=0 (Linux /dev/ttyS0 - Windows COM1)")
    parser.add_option("-b","--baud",action="store", type="int", dest="baud",
                      help="Baud rate to be used during the communication. "
                      "Default: BAUDRATE=115200")

    (options,args)=parser.parse_args()
    if options.filename!=None:
        GUI=False

    if options.port!=None:
        PORT=options.port
        GUI=False

    if options.baud != None:
        BAUDRATE=options.baud
        GUI=False
    #Iniciar la aplicacion grafica si esta definida
    if GUI:
        app = MyApp(0)
        app.MainLoop()
    else:
        
        #Ejecutar la aplicacion de consola
        if options.filename!=None:
            TransferFile(None,options.filename)
        else:
            if WXP==True:
                parser.error("\n\nError: When PORT or BAUDRATE are given,"
                             " FILENAME is a required parameter\n"
                             "To use the wxWidgets GUI, invoke the program"
                             " with no options\n\n")
            else:
                 parser.error("\n\nError: wxWidgets not found. To use the"
                              " console version FILENAME is required\n\n")

```

---

### Post by ferezvi on 2008-06-17
Hi; about picc18 under wine and piklab you can try to add the path of the executable directory and make sure to have the windows executable type enabled.

And about tiny pic bootloader you can run the tinybldWin.exe under wine, it works i explain how to on my web [http://fjv.awardspace.com/TPBL%20en%20Linux.html](http://fjv.awardspace.com/TPBL%20en%20Linux.html) it is in Spanish but if you can't understand it open a terminal and type:


$ cd ~/.wine/dosdevices

$ ln -s /dev/ttyUSB0 com1 

$ sudo chown `id -u -n` /dev/ttyUSB0

and the tinybldWin.exe will works as in windows, just one thing, if you are using the PICC-Lite you have tu add an interruption function

void interrupt my_isr(void){}

at the beginning always doesn't matter if you are using an isr or not

**ttyUSB0 is were my USB-SER converter is mounted, wish you luck :KS

---

### Post by rlameiro on 2008-06-17
> **gmagno said:**
> Hi,


By the way, i need a bootloader too, i've tryed to use Python interface for the Tiny Pic Bootloader  ([COLOR="Blue"]http://trac.cihologramas.com/pytbl[/COLOR]) but with no success, because i'm using a laptop and have no serial port (RS232) - i use a USB to RS232 converter (which works fine with other applications), but in this case this python application only permits connection to /dev/ttySx and no /dev/ttyUSBx... If anyone could look at the code a tell me what to change, that would be great (i've already tryed it...).

Thanks in advance

[PHP] for i in ("[SIZE="4"][COLOR="Red"]/dev/ttyUSB0","/dev/ttyUSB1","/dev/ttyUSB2[/COLOR][/SIZE]"):
        try:
            ser=serial.Serial(port=i)
            #ser.open()
            ser.close()
            seriales.append(str(i))
        except serial.SerialException:
            continue
    
    return seriales
[/PHP]

I would try to change the values in red, for the ones that you have on your computer.

Use the following script to search the available port that pyserial "can see"

[PHP]#!/usr/bin/env python
"""Scan for serial ports.
Part of pySerial (http://pyserial.sf.net)  (C)2002-2003 <cliechti@gmx.net>

The scan function of this module tries to open each port number
from 0 to 255 and it builds a list of those ports where this was
successful.
"""

import serial

def scan():
    """scan for available ports. return a list of tuples (num, name)"""
    available = []
    for i in range(256):
        try:
            s = serial.Serial(i)
            available.append( (i, s.portstr))
            s.close()   #explicit close 'cause of delayed GC in java
        except serial.SerialException:
            pass
    return available

if __name__=='__main__':
    print "Found ports:"
    for n,s in scan():
        print "(%d) %s" % (n,s)[/PHP]


hope this helps

---

### Post by ferezvi on 2008-06-18
> **Amazona aestiva said:**
> I've compiled the latest PikLab successfully, but I when I give it the path of the picc18 compiler it can't recognise it. It runs under wine.(Tested with MPLAB) 

Piklab wants an exe called picc18, but there is only mcc18.exe???

So I created a link to mcc with named picc, and still not recognised?!

Can anyone help me?

PS: In Piklab I can choose Unix/Windows c18 compiler, If there is a linux version, where would I find it?

I think you are trying to link the wrong compiler picc18 is made by Hi-tech and mplab-cl8( mcc18 ) is made by microchip, you have to choose C18 compiler instead of picc18.

---

