---
title: "Python treeview and recursion: help needed"
date: 2008-05-22
forum: Programming Talk
---

### Post by drakkan on 2008-05-22
Hi, 

I have a database with the following structure:

id    name  sublevel

for example

1     Node1     None
2     Node2     1
3     Node3     2
4     Node4     None
5     Node5     1
6     Node6     5
....
....


where Node1 and Node4 are treeview's master nodes, Node2 is a subnode of Node1, Node3 is a subnode of Node2, Node5 is a subnode of Node1 and Node6 a subnode of Node5 and so on

I need a recursive function to populate treeview and I'm stuck on this function :confused:

I need a list where I have the master node with child node inside and if a child node as others child nodes, I need thess nodes inside the child nodes.

Something like this:

[
{"id":1,"Childs":[{"id:2","Childs":[{"id":3,"Childs":[]}]},
{"id":5, "Childs":[{"id":6,"Childs":[]}]}]},{"id":4,"Childs":[]}  
]

any help is appreciated,

thanks drakkan

---

### Post by drakkan on 2008-05-23
Only for the records, here is a working solution

```


import sys
sys.path.append('/home/nicola/django/videosorveglianza')
from django.core.management import setup_environ
import settings
setup_environ(settings)
from django.conf import settings
from videosorveglianza.commands.Classi import *
from videosorveglianza.commands.models import *

zones=[]

def ottienifigli(zona):
	zone=Zone.objects.filter(sublivello_di=zona)
	figli=[]
	for z in zone:
		figli.append({
				'Zona_id':z.id,
				'Id_padre':z.sublivello_di.id,
		})
		ottienifigli(z)
	zones.append({
		'Zona_id':zona.id,
		'Figli':figli
	})

def rimuoviduplicati(lista):
	for s in lista:
		j=-1
		i=0
		for s1 in lista:
			j=j+1
			if s['Zona_id']==s1['Zona_id']:
				i=i+1
				if i >1:
					del lista[j]


listaid=[]
def generaid():
	zone=Zone.objects.all()
	# se il sublivello e' nullo allora e' una zona padre
	for zona in zone:
		#if zona.sublivello_di is None:
		listaid.append(zona.id)
	#print padri

padri=[]
def generapadri():
	zone=Zone.objects.all()
	# se il sublivello e' nullo allora e' una zona padre
	for zona in zone:
		if zona.sublivello_di is None:
			padri.append(zona.id)
	#print padri

def visitaalbero():
	zone=Zone.objects.all()
	for z in zone:
		ottienifigli(z)
	rimuoviduplicati(zones)
	print zones

visitaalbero()
generaid()
generapadri()

def accoppia(z):
	if z['Zona_id'] in listaid:
		i=-1
		for c in z['Figli']:
			i=i+1
			for z1 in zones:
				if c['Zona_id'] ==z1['Zona_id']:
					z['Figli'][i]=z1
					accoppia(z['Figli'][i])
	#print "\n\n\n\n"
	#print zones

def accoppianodi():
	for z in zones:
		accoppia(z)

darimuovere=[]
def childdarimuovere():
	i=-1
	for z1 in zones:
		i=i+1
		if z1['Zona_id'] not in padri:
			darimuovere.append(i)

accoppianodi()
print "\n\n\n\n"
print zones
print "\n\n\n\n"
childdarimuovere()
print darimuovere
k=-1
for s in darimuovere:
	k=k+1
	del zones[s-k]
	print s
	#print type(s)

print "\n\n\n\n"

print zones


```

---

