---
title: "Odd containment issue with Python"
date: 2007-08-05
forum: Programming Talk
---

### Post by marcos.linux on 2007-08-05
I am having an issue with containments under Python, my goal is to make python return "Cierto" whenever certain words are input by the user. Here is the code:

```

#!/usr/bin/env python
# Esto es solo un pequeno repaso del examen #1 que sera dado en la Interamericana el Lunes, 6 de agosto del 2007
# Escrito por Marcos Rodriguez <marcosrdz@gmail.com> <http://www.bashterritory.com> bajo la GPL v3
import sys
puntos=25

def preg1():
	global puntos
	print
	preg1=raw_input("Que es una computadora? ")
	preg1=preg1.lower()
	if "sistema electronico que lleva acabo operaciones de aritmetica" or "aritmetica" or "sistema que hace operaciones de logica" or "equipo electronico" or "logica" or "altas velocidades" or "alta velocidad" in preg1:
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	preg2()

def preg2():
	global puntos
	print
	print
        preg1=raw_input("Que es Hardware? ")
        if "equipo fisico" or "pieza fisica" or "fisico" in preg1:
                print "Cierto!"
        else:
		print "Falso!"
                puntos=puntos-1
        preg3()

def preg3():
        print
	global puntos
        preg1=raw_input("Que es Software? ")
        preg1=preg1.lower()
	if "programa de aplicacion" or "aplicacion" or "funcionamiento de una computadora" or "programa" or "instrucciones" in preg1:
                print "Cierto!"
        else:
		print "Falso!"
                puntos=puntos-1
        preg4()

def preg4():
        print
	global puntos
        preg1=raw_input("Que es Input? ")
	preg1=preg1.lower()
        if "unidad de entrada" or "entrada" in preg1:
                print "Cierto!"
        else:
		print "Falso!"
                puntos=puntos-1
        preg5()

def preg5():
	print
	global puntos
	preg1=raw_input("Que es Output? ")
	preg1=preg1.lower()
	if "unidad de salida" or "salida" in preg1:
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	preg6()

def preg6():
	global puntos
	print
	preg1=raw_input("Que es almacenamiento? ")
	preg1=preg1.lower()
	if "guarda datos" or "guarda" or "guarda informacion" or "mantiene" or "mantienen" or "estan" or "guarda la informacion" in preg1:
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	preg7()

def preg7():
	print
	global puntos
	preg1=raw_input("Que es procesamiento? ")
	preg1=preg1.lower()
	if "manejo" or "cambio" or "almacenamiento" or "info" or "informacion" or "transmiten" in preg1:
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	preg8()

def preg8():
	global puntos
	print
	preg1=raw_input("Menciona el nombre de la primera calculadora mecanica: ")
	preg1=preg1.lower()
	if "pascal" in preg1:
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	preg9()

def preg9():
	global puntos
	print
	preg1=raw_input("Quien es el padre de las computadoras? ")
	preg1=preg1.lower()
	if "babbage" in preg1:
		preg2=raw_input("Babbage es el apellido, pero cual es su nombre? ")
		preg2=preg2.lower()
		if preg2=="charles":
			print "Cierto!"
			preg10()
		else:
			print "Falso! Su nombre es Charles, Charles Babbage."
			puntos=puntos-1
			preg10()
	else:
		print "Falso!"
		puntos=puntos-1
		preg10()

def preg10():
	global puntos
	print
	preg1=str(raw_input("Cuantas generaciones existen de computadoras actualmente? "))
	preg1=preg1.lower()
	if preg1=="cinco" or "5":
		print "Cierto!"
		preg11()
	else:
		print "Falso!"
		puntos=puntos-1
		preg11()
def preg11():
	global puntos
	print
	print "Mencioname 2 lenguages de alto nivel mencionados en clase."
	preg1=raw_input("El Primero: ")
	preg2=raw_input("El Segundo: ")
	preg1=preg1.lower()
	preg2=preg2.lower()
	if preg1=="cobalt" or "c" or "c++" or "c plus plus" or "c mas mas" or "java" or "python":
		print "El primer lenguage especificado fue: " + preg1.title() + ", el cual esta correcto!"
	else:
		print "Falso!"
		puntos=puntos-1
	if preg2=="cobalt" or "c" or "c++" or "c plus plus" or "c mas mas" or "java" or "python":
                print "El segundo lenguage especificado fue: " + preg2.title() + ", el cual esta correcto!"
                preg12()
        else:
                print "Falso!"
		puntos=puntos-1
                preg12()
def preg12():
	print
	global puntos
	print "Mencioname dos sistemas operativos"
	preg1=raw_input("El Primero: ")
	preg2=raw_input("El Segundo: ")
	preg1=preg1.lower()
        preg2=preg2.lower()
        if preg1=="linux" or "unix" or "windows" or "macintosh" or "os x" or "osx" or "macosx":
                print "El primer sistema operativo especificado fue: " + preg1.title() + ", el cual esta correcto!"
        else:
                print "Falso!"
                puntos=puntos-1
        if preg2=="linux" or "unix" or "windows" or "macintosh" or "os x" or "osx" or "macosx":
                print "El segundo sistema operativo especificado fue: " + preg2.title() + ", el cual esta correcto!"
                preg13()
        else:
                print "Falso!"
		puntos=puntos-1
                preg13()
def preg13():
	print
	global puntos
	preg1=raw_input("Que es un programa de aplicacion? ")
	preg1=preg1.lower()
	if preg1=="conjunto de instrucciones" or "instrucciones" or "ejecute" or "determinadas" or "operaciones":
		print "Cierto!"
		preg14()
	else:
		print "Falso!"
		puntos=puntos-1
		preg14()
def preg14():
	print
	global puntos
	print "Listado: "
	print "-----------------------" 
	print
	print "1) Windows"
	print "2) Linux"
	print "3) Firefox"
	print "4) Microsoft Office"
	print "5) OpenOffice"
	print "6) Unix"
	preg1=str(raw_input("Cual de esa lista mencionada es un programa de aplicacion? "))
	preg1=preg1.lower
	if preg1=="openoffice" or "microsoft office" or "firefox":
		print "Cierto!"
		preg15()
	elif preg1=="unix" or "linux" or "windows" or "freebsd" or "qnx" or "os2":
		print "Falso! Eso es un sistema operativo."
		puntos=puntos-1
		preg15()
def preg15():
	print
	global puntos
	preg1=raw_input("Como se llama la activacion de una computadora al estar apagada? ")
	preg1=preg1.lower()
	if preg1=="coldstart":
		print "Cierto!"
		preg16()
	else:
		print "Falso!"
		puntos=puntos-1
		preg16()
def preg16():
	print
	global puntos
	preg1=raw_input("Como se llama la activacion de una computadora al ser reiniciada? ")
	preg1=preg1.lower()
	if preg1=="warmstart":
		print "Cierto!"
		preg17()
	else:	
		print "Falso!"
		puntos=puntos-1
		preg17()

def preg17():
	print
	global puntos
	print "Mencione en orden, como se llaman los archivos que al Microsoft Windows iniciar busca."
	print "-----------------------------------------------------------------------------------------------"
	opt1=raw_input("Primeros 2 archivos: ")
	opt1=opt1.lower()
	if opt1=="io.sys" or "dos.sys":
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	opt2=raw_input("Proximos 3 archivos: ")
	opt2=opt2.lower()
	if opt2=="io" or "command.com" or "dos":
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	opt3=raw_input("Que es lo que la computadora hace con estos archivos? ")
	opt3=opt3.lower()
	if opt3=="guarda en el ram" or "guarda" or "ram":
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	opt4=raw_input("Cual archivo Windows accesa para leer la configuracion? ")
	opt4=opt4.lower()
	if opt4=="config.sys":
		print "Cierto!"
	else:
		print "Falso!"
		puntos=puntos-1
	opt5=raw_input("Cual es el ultimo archivo ejecutado antes de Windows iniciar? ")
	opt5=opt5.lower()
	if opt5=="autoexec.bat":	
		print "Cierto!"
		final()
	else:
		print "Falso!"
		puntos=puntos-1
		final()

def final():
	print
	print
	global puntos
	print
	print "-------------------------------------------------------------------------------------"
	print nombre + " " + apellido + ", tu puntualidad final ha sido: " + str(puntos) + "/25."


def listadoexamen():
	print
	print """Estas preguntas, son las que te hare:

		 1) Que es una computadora
		 2) Que es Hardware
		 3) Que es Software
		 4) Que es Input
		 5) Que es Output
		 6) Que es almacenamiento
		 7) Que es procesamiento
		 8) El nombre de la primera calculadora mecanica
		 9) Quien es el padre de las computadoras
		 10)Cuantas generaciones existen de computadoras
		 11) Menciona almenos 2 lenguages de alto nivel que existen
		 12) Nombre 2 sistemas operativos mas famosos
		 13) Que es un programa de aplicacion
		 14) Mencione un programa de aplicacion
		 15) Como se llama la activacion de la computadora al estar apagada
		 16) Como se llama la activacion de la computadora al ser reiniciada
		 17) Nombre y orden de los archivos accesados al Microsoft Windows ser iniciado
	 """ 
	tomarlo()	
def reglas():
	print """
		 1) Este examen tiene un valor de 25 puntos
		 2) Puedes contestar las preguntas en mayuscula o minuscula, no tiene importancia
	 	 3) Este programa intentara buscar una similitud entre lo que usted responda y lo que tengo en mi database, intenta contestar lo mas exacto posible
		 4) Usted tiene que escribir la contestacion manualmente
	"""
def tomarlo():
	tomarlo=raw_input("Deceas tomar este examen ahora? ")
        if tomarlo=="Si":
                print
                preg1()
        elif tomarlo=="No":
                sys.exit
        else:
                print 
    		print "Contesta con un Si o con un No"
		tomarlo()


print "Examen #1 - Programa escrito por Marcos Rodriguez - email: marcosrdz@gmail.com"
print "----------------------------------------------------------------------"
print 
nombre=raw_input("Escriba su nombre: ")
apellido=raw_input("Escribe su apellido: ")
print
print "Hola " + nombre+ " " + apellido + "!" 
bienvenida=raw_input("Deceas ver el listado del contenido de este examen? ")
bienvenida=bienvenida.upper()
if bienvenida=="SI":
	listadoexamen()
elif bienvenida=="NO":
	print 
	print preg1()
else:
	print preg1()

```


So as you can see if the user inputs  "alta velocidad" OR "altas velocidades" I want python to return "CIerto!" but instead I get "Cierto!" even if the user inputs ANYTHING at all. :confused:

---

### Post by Mirrorball on 2007-08-05
I think it should be:
```

if "sistema electronico que lleva acabo operaciones de aritmetica" in preg1 or "aritmetica" in preg1 or "sistema que hace operaciones de logica" in preg1:

```You should also think about another design for your script, because it's going to get very hard to maintain. There is too much duplicated code. Whenever you write a program, remember the program design principle "Don't Repeat Yourself" (DRY).

Consider storing all questions and answers in plain text format in a separate file. Then make a script that reads this file, builds the questions and prompts the user to answer them.

---

### Post by pmasiar on 2007-08-05
> **marcos.linux said:**
> I am having an issue with containments under Python, my goal is to make python return "Cierto" whenever certain words are input by the user. 
...

So as you can see if the user inputs  "alta velocidad" OR "altas velocidades" I want python to return "CIerto!" but instead I get "Cierto!" even if the user inputs ANYTHING at all. :confused:

1) Next time, create simplified example.  For big examples, even consider translating variable names to english - so it will be easier to follow your logic. It will save time to *us* -- so more people might be willing to look and help you. Make it easy for us to help you! :-)

2) What is your definition of "containment"? 

3) From brief look your code *prints* "cierto" instead of returning it :-) Which function is it?

4) Also, it is good idea to avoid big magic strings like you have, put those texts into some array -- it will be easier to code now, and to change/extend later.

---

