---
title: "objectlist kiwi  + Pygtk  + glade3 + Postgres 8"
date: 2009-06-28
forum: Programming Talk
---

### Post by Patagon on 2009-06-28
I'm using Ubuntu 9.04 with NetBeans editor, Postgres 8.3, PyGtk, Glade3 and kiwi
	
I'm stuck

I need do this:

When I double click in the kiwi objectlist (the grid) I need the value of the cell Dni (in this case the id) or I need the content of the cell where I clicked.

I obtain the name of the object but no the contents of cell ( I need the content)

image:
[http://img35.imageshack.us/i/pantallazobasesdedatos.png/](http://img35.imageshack.us/i/pantallazobasesdedatos.png/)

[IMG]http://img35.imageshack.us/i/pantallazobasesdedatos.png/[/IMG]

If exists a solution without kiwi, better..

[PHP]#!/usr/bin/python
# -*- coding: utf-8 -*-

import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade
import sys
import psycopg2
from kiwi.ui.objectlist import Column, ObjectList, ColoredColumn, SummaryLabel, SequentialColumn
from kiwi.ui.libgladeloader import LibgladeWidgetTree


class Base:
    def __init__(self, dni, nombre, departamento):
        self.dni = dni
        self.nombre = nombre
        self.departamento = departamento

class App:
    def __init__(self):
        self.gladefile = "main.glade"
        self.glade = gtk.Builder()
        self.glade.add_from_file(self.gladefile)

        global datos
        datos = ObjectList([
                    ColoredColumn('dni', data_type=int, sorted=True, color='red', data_func=color),
                    Column('nombre', data_type=str, tooltip='Este es el nombre'),
                    Column('departamento', data_type=str)
                    ])
       
        try:
            global conn
            conn = psycopg2.connect("dbname='prueba' user='postgres' host='localhost' password='anypass'");
            curs = conn.cursor()

            ubicacion2 = str(ubicacion)
            curs.execute("SELECT * FROM ""prueba"" order by 1 offset " + ubicacion2 + " limit 7")
            rows = curs.fetchall()
            for i in range(len(rows)):
                print "dni", i, "nombre", rows[i][0], "departamento", rows[i][1]
        except:
            print "no me puedo conectar"
        i = 0
        for i in ((rows)):
            datos.append(Base(i[0], i[1], i[2]))
     
        window = self.glade.get_object("mainwindow")
        treev = self.glade.get_object("frame1")
        treev.add(datos)

        window.show_all()
        self.glade.connect_signals(self)
        conn.close()

    def on_salir_clicked(self, widget): #salir
        gtk.main_quit()


if __name__ == "__main__":
    try:
        a = App()
        gtk.main()
    except KeyboardInterrupt:
        pass[/PHP]




Bye

---

### Post by Patagon on 2009-07-08
I reply to myself

[PHP]

#in 
class App:
    def __init__(self):        
    ...
    ...
    ...
    ...
    datos.connect("row-activated", self.doble_click) #add this line
    window.show_all()
    self.glade.connect_signals(self)
    conn.close()



    def doble_click(self, dni, departamento):
        global datos
        modificar = datos.get_selected()
        cosa2 = modificar.dni  #get the "dni" value
        print cosa2 #use the "dni" value


[/PHP]

---

