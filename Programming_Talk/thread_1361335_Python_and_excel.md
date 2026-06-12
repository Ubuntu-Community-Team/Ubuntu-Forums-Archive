---
title: "Python and excel"
date: 2009-12-21
forum: Programming Talk
---

### Post by Atzu on 2009-12-21
Hello everyone! 

I'd like to know if I could make a program that is able to add stuff to excel... Well... I know it's possible ... I'm asking what I need to do with python and if you know any tutorial or could explain me a bit about it... I want to make a program (without GUI I don't really care about that right now) that is able to add some stuff about people... like this:

| Name | Place | Phone | More stuff | More stuff |
--------------------------------------------------


Now i need that python ask for Name... Place... Phone... and the other stuff... I can make python ask for that... what i need is that python add it to a xls file in correct order so if you could help me thanks a lot!!

---

### Post by TheStatsMan on 2009-12-21
Have a look at  [http://www.python-excel.org/](http://www.python-excel.org/)

---

### Post by fiddler616 on 2009-12-21
> **TheStatsMan said:**
> Have a look at  [http://www.python-excel.org/](http://www.python-excel.org/)
This is probably the solution, but if you don't want to mess with third-party libraries, and you just need to use Python to put stuff into an Excel spreadsheet, you can create a .csv (comma-separated value) file using Python's native file-handling, and then import it in Excel.

Forget I said that. Use the library.

---

### Post by Atzu on 2009-12-21
haha nice thanks a lot... I see that i use this to write to cells: 

sheet1.write(0, 0, "This is the First Cell of the First Sheet") 

in which 0's are rows and columns... is there a way they go like 0, 1... 0,2... and so on for my program? like... It ask for names... and all names should go: 0,1 0,2 0,3 0,4 .... and etc for x numbers of names... and Phones should go 1,1 1,2 1,3 ,1,4 and stuff like that? if you could help I'd love it~ thanks... I'm only 16 years old.. :/ self learning is a bit hard for me...

---

### Post by fiddler616 on 2009-12-22
> **Atzu said:**
> haha nice thanks a lot... I see that i use this to write to cells: 

sheet1.write(0, 0, "This is the First Cell of the First Sheet") 

in which 0's are rows and columns... is there a way they go like 0, 1... 0,2... and so on for my program? like... It ask for names... and all names should go: 0,1 0,2 0,3 0,4 .... and etc for x numbers of names... and Phones should go 1,1 1,2 1,3 ,1,4 and stuff like that? if you could help I'd love it~ thanks... I'm only 16 years old.. :/ self learning is a bit hard for me...
OK.

First, read [this]("http://www.ibiblio.org/swaroopch/byteofpython/read/for-loop.html"). I don't want to give the answer away, but think about the following:
[LIST]
[*]What numbers are changing?
[*]How can they be expressed as variables (as in: which ones should be combined into one variable)?
[*]How can you have the variable change as needed? Will you use a loop? How?
[/LIST]

Then write some code, test it, and come back here to tell use how it worked--then we can give you some more hints as necessary. Even if it works, we may be able to make it more elegant.



I'm 16 too, and owe my knowledge of Python (and, to a lesser extent, Java) to this forum. In the summer of '08 I crawled through the Python tutorial I linked to above, experimented, made mistakes, asked amateur questions on the forums, was very polite and appreciative to those who helped me, and now they seem to have left (nvteighen, ¡te extraño! pmasiar, where'd you go&#8253; LaRoza, why'd you let yourself get banned?) And now **I'm** helping people. That's scary. Forgive my old-man-style reminiscences, but the moral to the story is to look past the short-term (solving your Excel problem) and using this great community to help you become a better programmer. I will not tolerate any "I'm too you and stupid" ridiculousness.

PS: Veo que vives en Costa Rica...¿supongo qué hablas español? Yo nací en Tegucigalpa, Honduras, y viví allí para nueve años. Y el año pasado viví en Madrid para seis meses.

---

### Post by Atzu on 2009-12-22
Heh... Thanks a lot... I'll continue this tomorrow morning I want to do this to make easier something my dad asked to me xD... So it isn't really necessary... still if i dont make it at time I'll want to finish this later it may help my dad for doing this again next month lol... 

PS: Si hablo español gusto en conocerte y gracias por la ayuda ^^ pero aqui ya es tarde y puedo continuar mañana. Gracias :P No creo que sea tan dificil lo que ocupo... Jaja

---

### Post by CptPicard on 2009-12-22
> **fiddler616 said:**
> ...pmasiar, where'd you go&#8253;

... banned, due to one too many a clash with the pointer-crowd :(

At least LaRoza is around LambdaGrok (see my sig, I guess I'll plug that place a bit although it's relatively quiet), and even pmasiar theoretically is, although he's very busy in his real-life atm.

---

### Post by fiddler616 on 2009-12-22
> **CptPicard said:**
> ... banned
This is what they call, "Cutting off your nose to spite your face."

But I won't get too vocal, lest I get myself into trouble.

And I've thought about joining LambdaGrok, but I always thought that I should learn Lisp first.

Returning to the problem at hand...Atzu needs to post back.

And for all you non-Spanish speakers, we just had a little "I see you're from Costa Rica. I was born in Honduras. Do you speak Spanish?" "Why yes I do! And thanks for your help." moment.

---

### Post by Can+~ on 2009-12-22
Y derrepente todos saben hablar español.

:???:

Yo me hubiera ido por la ruta del .csv, mas que nada, porque es mas portable, quien sabe como interpretará excel u openoffice.

---

### Post by Atzu on 2009-12-22
hmm so... i think i made something good... but i have a problem now lol... maybe you will think my programming code is poor and a bit stupid but well im learning ~ xD 

```
 
import xlwt 
from datetime import date


now = date.today()


book = xlwt.Workbook(encoding="utf-8") 



sheet1 = book.add_sheet("Ck 9201451") 
sheet2 = book.add_sheet("Ck 29 9") 
sheet3 = book.add_sheet("Fac 666234") 

Fecha = []
Boleta = []
Departamento = []
Pasajeros = []
Provincia = []
Direccion = []
Recorrido = []
Monto = []
Taxi = []

a = 0

print "Hoja # 1 = Ck 9201451"
print "Hoja # 2 = Ck 29 9"
print "Hoja # 3 = Fac 666234"

w = input("Hoja #: ")


while a != "hecho":
	a = raw_input("Fecha: ")
	Fecha.append(a)
	
	#b = input("Boleta: ")
	#Boleta.append(b)
	
	#c = raw_input("Depto: ")
	#Departamento.append(c)
	
	#d = raw_input("Pasajeros: ")
	#Pasajeros.append(d)
	
	#e = raw_input("Provincia: ")
	#Provincia.append(e)
	
	#f = raw_input("Direccion: ")
	#Direccion.append(f)
	
	#g = raw_input("millas? si/no: ")
	#if g == "si":
	#	l = input("Recorrido: ") * 1.609344
	#else:
	#	l = input("Recorrido: ")
	#Recorrido.append(l)
	
	#h = input("Monto: ")
	#Monto.append(h)
	
	#i = input("Taxi: ")
	#Taxi.append(i)
	
	q = input("Exit? 1 = y 2 = n: ")
	if q == 1:
		a = "hecho"
	else:
		a = 0
	
	h = len(Fecha)
	for k in range(0, h):
		if w == 1:
			w = sheet1
		elif w == 2:
			w = sheet2
		elif w == 3:
			w = sheet3
		w.write(h, 1, Fecha[len(Fecha)-1])
		#w.write(h, 2, Boleta[len(Boleta)-1]) 
		#w.write(h, 3, Departamento[len(Departamento)-1]) 
		#w.write(h, 4, Pasajeros[len(Pasajeros)-1]) 
		#w.write(h, 5, Provincia[len(Provincia)-1]) 
		#w.write(h, 6, Direccion[len(Direccion)-1]) 
		#w.write(h, 7, Recorrido[len(Recorrido)-1]) 
		#w.write(h, 8, Monto[len(Monto)-1]) 
		#w.write(h, 9, Taxi[len(Taxi)-1]) 
		book.save("wiii "+now.strftime("%m-%d-%y")+".xls")

```

All the commented stuff is for testing... with testing the Date cell is enough :p when i run that it works and add stuff how i want but when i add the second date i get this:

```

Traceback (most recent call last):
  File "untitled2.py", line 81, in <module>
    w.write(h, 1, Fecha[len(Fecha)-1])
  File "/usr/lib/pymodules/python2.6/xlwt/Worksheet.py", line 1002, in write
    self.row(r).write(c, label, style)
  File "/usr/lib/pymodules/python2.6/xlwt/Row.py", line 233, in write
    StrCell(self.__idx, col, style_index, self.__parent_wb.add_str(label))
  File "/usr/lib/pymodules/python2.6/xlwt/Row.py", line 152, in insert_cell
    raise Exception(msg)
Exception: Attempt to overwrite cell: sheetname=u'Ck 9201451' rowx=2 colx=1

```

I don't really get how im trying to overwrite that cell... 
If you could help me i'd be really happy :D >.> Thanks~

---

### Post by Can+~ on 2009-12-22
```
w.write(h, 1, Fecha[len(Fecha)-1])
```

You exactly mentioned above that:

```
sheet1.write(**0, 0**, "This is the First Cell of the First Sheet") 
```

Being that 0,0, the row/col on the worksheet.

Now, take a moment, and notice that, after the second iteration of the while-loop, the h remains constant (and 1 too, of course).

---

### Post by fiddler616 on 2009-12-22
Can+~: &#11800;Tú también&#8253; Que va...

Aztu: Can+~ is right. That said, I have two general tips:

1) Your procedure for exiting the loop is a bit clunky. q and a serve the same purpose and should be combined. Actually, the better solution would be to use a
[PHP]break[/PHP]

2) [PEP 8]("http://www.python.org/dev/peps/pep-0008/") is the Python Bible of Style. I recommend reading it...about once a month...but the key quote at the moment is:
>     Python coders from non-English speaking countries: please write
    your comments in English, unless you are 120% sure that the code
    will never be read by people who don't speak your language.


You lucked out in that hispanohablantes came out of the woodwork to help you, but for future reference I would recommend using variables like date and passengers instead of Fecha and Pasajeros if you plan on showing your code to anyone else. If that sounds angry or reprimanding, I'm sorry--I'm very happy, nay, ecstatic that you produced almost-working code, are willing to receive help, and acknowledge that good style is important, albeit currently lacking.

---

### Post by Atzu on 2009-12-22
```

import xlwt 
from datetime import date

now = date.today()

book = xlwt.Workbook(encoding="utf-8") 


sheet1 = book.add_sheet("Ck 9201451") 
sheet2 = book.add_sheet("Ck 29 9") 
sheet3 = book.add_sheet("Fac 666234") 

Fecha = []
Boleta = []
Departamento = []
Pasajeros = []
Provincia = []
Direccion = []
Recorrido = []
Monto = []
Taxi = []

a = 0

print "Hoja # 1 = Ck 9201451"
print "Hoja # 2 = Ck 29 9"
print "Hoja # 3 = Fac 666234"

w = input("Hoja #: ")
if w == 1:
	w = sheet1
elif w == 2:
	w = sheet2
elif w == 3:
	w = sheet3


while a != "hecho":
	h = len(Fecha) + 2
	a = raw_input("Fecha: ")
	Fecha.append(a)
	w.write(h, 0, Fecha[len(Fecha)-1])
	
	b = input("Boleta: ")
	Boleta.append(b)
	w.write(h, 1, Boleta[len(Boleta)-1])

	c = raw_input("Depto: ")
	Departamento.append(c)
	w.write(h, 2, Departamento[len(Departamento)-1])
	
	d = raw_input("Pasajeros: ")
	Pasajeros.append(d)
	w.write(h, 3, Pasajeros[len(Pasajeros)-1])
	
	e = raw_input("Provincia: ")
	Provincia.append(e)
	w.write(h, 4, Provincia[len(Provincia)-1])
	
	f = raw_input("Direccion: ")
	Direccion.append(f)
	w.write(h, 5, Direccion[len(Direccion)-1])
	
	g = raw_input("millas? si/no: ")
	if g == "si":
		l = input("Recorrido: ") * 1.609344
	else:
		l = input("Recorrido: ")
	Recorrido.append(l)
	w.write(h, 6, Recorrido[len(Recorrido)-1])
	
	h = input("Monto: ")
	Monto.append(h)
	w.write(h, 7, Monto[len(Monto)-1])
	
	i = input("Taxi: ")
	Taxi.append(i)
	w.write(h, 8, Taxi[len(Taxi)-1]) 
	
	q = input("Salir? 1 = n 2 = y: ")
	if q == 2:
		a = "hecho"
	else:
		a = 0
	book.save("Taxi GSI "+now.strftime("%m-%d-%y")+".xls")

```

It looks like that one work... now some questions... do you find a smarter way to exit? like... is it too hard that if i press a key combination it exit? other than having to press 1 every time i want to continue ? >_>;; and another one...

```

	g = raw_input("millas? si/no: ")
	if g == "si":
		l = input("Recorrido: ") * 1.609344

```
That should convert miles to kms right? xD Thanks~

---

### Post by fiddler616 on 2009-12-22
> **Atzu said:**
> 

It looks like that one work... now some questions... do you find a smarter way to exit? like... is it too hard that if i press a key combination it exit? other than having to press 1 every time i want to continue ? >_>;; and another one...

```

	g = raw_input("millas? si/no: ")
	if g == "si":
		l = input("Recorrido: ") * 1.609344

```
That should convert miles to kms right? xD Thanks~

I briefly addressed exiting above in terms of code mechanics. In terms of UI, I sometimes have something like this, at the beginning of the loop:
```

a = raw_input("Fecha ('hecho' para salir) : ")
if a == 'hecho':
    break

```
Other solutions involve using the curses library so that pressing Esc or something will stop the program (do not go down this road, I'm just saying it's an option), or just letting it loop infinitely and relying on the Ctrl-C combination built into terminals to halt execution. Which is a bit hackish. It's up to you. To be honest, I'd be interested to hear what someone else has to say on this.

Your bit about converting to km looks fine, except I would use:
```
if g.lower() == "si":
```
just in case. Also, it will break if the user types in "sí" (which is correct), but Python's unicode support is not something I know enough about to discuss thoroughly, and it's all changing in Python 3000.

---

### Post by Can+~ on 2009-12-22
[PHP]#!/usr/bin/env python

import xlwt 
from datetime import date

# Constantes
KWQUIT = "salir" # palabra para salir del programa
MILESCONV = 1.609344

# El libro a utilizar
book = xlwt.Workbook(encoding="utf-8")

# El listado de hojas
sheets = ["Ck 9201451", "Ck 29 9", "Fac 666234"]

tmp = []
for sheet in sheets:
	tmp.append(book.add_sheet(sheet))

# Ahora, en vez de guardar los nombres, guardar las referencias
sheets = tmp

# Especificar las columnas
columns = {
	"fecha":[],
	"boleta":[],
	"departamento":[],
	"pasajeros":[],
	"direccion":[],
	"recorrido":[],
	"monto":[],
	"taxi":[]
}

print "Hoja # 1 = Ck 9201451"
print "Hoja # 2 = Ck 29 9"
print "Hoja # 3 = Fac 666234"

# Guardar la hoja a utilizar
inp = int(raw_input("Hoja #: "))
currentsheet = sheets[inp]

# Preguntar si va a usar millas
inp = raw_input("Desea utilizar millas (s/n)?: ")
multiplier = 1

if inp == 's':
	multiplier = MILESCONV

# Escribir la primera columna con las cabeceras
for (colcount, column) in enumerate(columns):
	currentsheet.write(0, colcount, column)

# La fila actual
currentrow = 1

print "Recuerde: Escriba {0} para salir".format(KWQUIT)

while True:
	
	# Pedir todas las columnas
	for column in columns:
		
		# pedir la columna deseada
		inp = raw_input("{0}: ".format(column.title()))
		
		# salir
		if inp == KWQUIT:
			break
		
		# hacer conversion a millas
		if column == "recorrido":
			inp = str(int(inp)*multiplier)
		
		# Guardar el dato
		columns[column].append(inp)
	
	# otro salir para romper el loop principal
	if inp == KWQUIT:
		break
	
	# Guardar las columnas en el excel
	for (colcount, column) in enumerate(columns):
		currentsheet.write(currentrow, colcount, columns[column].pop())
	
	# Agregar uno a la columna, para desplazarla
	currentrow += 1

# Hacer esto al final
book.save("wiii "+date.today().strftime("%m-%d-%y")+".xls")
[/PHP]

This is basically the same code, although I added some data structures, and better flow control, less use of variables.

I tried to limit myself to the basics of python (without OOP, or Functional paradigm), and avoid using other libraries, so to keep it newbie-friendly.

There are still a lot of new concepts introduced in the above piece of code, enumerate tuples, dictionaries, queues, and working better with the for..in loop.

(Also, I used a list inside the dictionary, not that necessary, as it always will hold at most, one value, but it just to introduce the idea of that you can "nest" data structures in python).

---

### Post by Atzu on 2009-12-22
Thanks for your help~ if you don't mind I'd like to use my own code :p I'd feel bad if i use that code xD ... for exit i think ill use the break thing~ 

For the Spanish thing... I'm sorry... I made it Spanish because you guys were helping and I actually didn't think about that... 

I'll post again here if I have another problems...

Thanks a lot guys~ also if you have another tips for me I'll take them happily :p Thanks!!

---

### Post by Atzu on 2009-12-22
Hmm ... i have another problem :/ for some reason im not able to understand 

the code (the same as before...) don't add the last 2 cells... after the miles thing ...


forget that~ i fixed it... i assigned h to another thing so it changed and didnt add the cell :/

Thanks for everything again!!~

---

### Post by fiddler616 on 2009-12-22
Great! I'm glad I could help.

Your final step: Marking the thread as solved.

---

