---
title: "Python PyGTK help"
date: 2010-02-10
forum: Programming Talk
---

### Post by Dan_Dranath999 on 2010-02-10
Hello people!
I'm starting to learn Python (2 weeks now) and my first project is a LAMPP Frontend (like the one in WAMPP) so i started looking at PyGTK, some tutorials and ended up with this:
(some comments and variables are still in spanish. I thought a good way to learn the code could be translating the comments and variables)

```

&#65279;#!/usr/bin/python
import gtk
import subprocess

class Mi_jodida_ventana(gtk.Window):

    def misOpz(self, widget, llamada, argz):
        print argz[2]
        def anyadirTxt(cajaTexto, bufferTexto, elTexto):
            NeuLinea = "\n" + elTexto
            end_iter = bufferTexto.get_end_iter()
            bufferTexto.insert(end_iter, NeuLinea)
            cajaTexto.scroll_to_mark(bufferTexto.get_insert(), 0)
            
        if llamada == "iniciar":
            anyadirTxt(argz[0], argz[1], argz[2])
            #self.cod1 = subprocess.call(["gksudo", "/opt/lampp/lampp", "start"])
            cod1 = subprocess.Popen(["gksudo", "/opt/lampp/lampp", "start"], stdout=subprocess.PIPE)
            cod1.wait()
            data1 = cod1.stdout.read()
            anyadirTxt(argz[0], argz[1], data1)
        elif llamada == "reiniciar":
            anyadirTxt(argz[0], argz[1], argz[2])
            #self.cod2 = subprocess.call(["gksudo", "/opt/lampp/lampp", "restart"])
            cod2 = subprocess.Popen(["gksudo", "/opt/lampp/lampp", "restart"], stdout=subprocess.PIPE)
            cod2.wait()
            data2 = cod2.stdout.read()
            anyadirTxt(argz[0], argz[1], data2)
        elif llamada == "detener":
            anyadirTxt(argz[0], argz[1], argz[2])
            #self.cod3 = subprocess.call(["gksudo", "/opt/lampp/lampp", "stop"])
            cod3 = subprocess.Popen(["gksudo", "/opt/lampp/lampp", "stop"], stdout=subprocess.PIPE)
            cod3.wait()
            data3 = cod3.stdout.read()
            anyadirTxt(argz[0], argz[1], data3)
        else:
            pass
    
    def cerrarVentana(self, widget, data=None):
        #print "Se cierra la ventana"
        gtk.main_quit()
        
    def __init__(self):
        super(Mi_jodida_ventana, self).__init__()
        self.set_title("LAMPP del Mexikan")
        self.set_size_request(500, 600)
        self.set_resizable(False)
        self.set_border_width(15)
        self.set_position(gtk.WIN_POS_CENTER)
        self.modify_bg(gtk.STATE_NORMAL, gtk.gdk.color_parse("#999999"))

        
        #==== main Column (Vertical Box)
        ColumnaPrincipal = gtk.VBox (False, 0);
        self.add(ColumnaPrincipal)
        
        CajaAreaTexto = gtk.VBox(False, 10)
        CajaAreaTexto.set_border_width(10)
        ColumnaPrincipal.pack_start(CajaAreaTexto, True, True, 0)
        
        areaDesplazable = gtk.ScrolledWindow()
        areaDesplazable.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        txt = gtk.TextView()
        textbuffer = txt.get_buffer()
        
        txt.set_pixels_above_lines(0)
        txt.set_pixels_below_lines(0)
        txt.set_left_margin(10)
        txt.set_right_margin(10)
        txt.set_editable(False)
        txt.set_cursor_visible(True)
        txt.set_wrap_mode(gtk.WRAP_WORD)
        txt.set_justification(gtk.JUSTIFY_LEFT)
        
        txt.modify_base(gtk.STATE_NORMAL, gtk.gdk.color_parse("black"))
        txt.modify_text(gtk.STATE_NORMAL, gtk.gdk.color_parse("green"))
        areaDesplazable.add(txt)

        CajaAreaTexto.pack_start(areaDesplazable)
        # Load the file textview-basic.py into the text window
        infile = open("/opt/lampp/gui/start.txt", "r")

        if infile:
           string = infile.read()
           infile.close()
           textbuffer.set_text(string)
        
        separador = gtk.HSeparator()
        ColumnaPrincipal.pack_start(separador, False, True, 0)

        #Button images
        img_ini = gtk.Image()
        img_ini.set_from_file("/opt/lampp/gui/btn_iniciar_a.png")
        img_det = gtk.Image()
        img_det.set_from_file("/opt/lampp/gui/btn_detener_a.png")
        img_rec = gtk.Image()
        img_rec.set_from_file("/opt/lampp/gui/btn_recargar_a.png")
        img_crr = gtk.Image()
        img_crr.set_from_file("/opt/lampp/gui/btn_apagar_a.png")
        
        #========== create buttons
        btn1 = gtk.Button()
        btn1.add(img_ini)
        btn2 = gtk.Button()
        btn2.add(img_det)
        btn3 = gtk.Button()
        btn3.add(img_rec)
        btn_cerrar = gtk.Button()
        btn_cerrar.add(img_crr)
        #tamaños de los botones
        btn1.set_size_request(105, 105)
        btn2.set_size_request(105, 105)
        btn3.set_size_request(105, 105)
        btn_cerrar.set_size_request(105, 105)
        
        btn1.connect("clicked", self.misOpz, "iniciar", [txt, textbuffer, "--> Iniciar el Servidor..."])
        btn2.connect("clicked", self.misOpz, "detener", [txt, textbuffer, "--> Detener el Servidor..."])
        btn3.connect("clicked", self.misOpz, "reiniciar", [txt, textbuffer, "--> Reiniciar el Servidor..."])
        btn_cerrar.connect("clicked", self.cerrarVentana, None)
        
        #crear caja para los botones (gtk.HButtonBox )
        cajaBotones = gtk.HButtonBox()
        
        
        cajaBotones.add(btn1)
        cajaBotones.add(btn2)
        cajaBotones.add(btn3)
        cajaBotones.add(btn_cerrar)
        
        ColumnaPrincipal.pack_start(cajaBotones, False, True, 5)
        
        self.connect("destroy", gtk.main_quit)
        
        #show all elements
        self.show_all()

Mi_jodida_ventana()
gtk.main()

```

So the thing works, but i suppose it could work better:
You can see i started calling lampp with "subprocess.call", but changed it to "subprocess.Popen" so i could capture the output and write it in the text field. **But the app freezes, and writes the output until the process is over.** i'd like that the output could write every line as it is generated, not until the process ends.

Other thing, i have to use absolute path to my button images: when calling my script like this: python /path/to/my/app/lamppGUI.py, the script wouldn't find them even if they are in the same folder. (How can i get the current path?)

Any help is appreciated.

---

### Post by Dan_Dranath999 on 2010-02-10
this is what the th¡ng looks like:
[IMG]http://ubuntuforums.org/picture.php?albumid=1665&pictureid=5608[/IMG]

---

### Post by Dan_Dranath999 on 2010-02-11
bump

---

### Post by goombah88 on 2012-02-13
I know it's a bit late, and you probably already found the answer, but you have to use threading to update the GUI while work is being done.  Google for "pygtk threading" and start from there.

Essentially you'll launch the work in a new thread and then use gobject.idle_add calls to update the GUI.

---

