---
title: "Python ---- Objectos"
date: 2009-03-23
forum: Programming Talk
---

### Post by onnix on 2009-03-23
Greetings 

Here is a module for card game that i have been working on, it returns an __str__ error of None type, need some help:



# Modulo Cartas

class Carta(object):
    """ Um baralho """
    
    NUMERO = ["A", "2", "3", "4", "5", "6", "7",
             "8", "9", "10", "J", "Q", "K"]
    NAIPE = ["e","p","c","o"]
    
    def __init__(self, numero, naipe):
        self.numero = numero
        self.naipe = naipe
        
    def __str__(self):
        rep = ""
        rep += self.numero + self.naipe
        return rep
    
    
class Baralho(object):
    """Um conjunto de 52 cartas."""
    
    def __init__(self):
        self.baralho = []

    def populate(self):
        for num in Carta.NUMERO:
            for naip in Carta.NAIPE:
                self.baralho.append(Carta(num,naip))
        
    def __str__(self):
        if self.baralho:
            rep = ""
            for carta in self.baralho:
                rep += str(carta)
        else:
            rep += "vazio"
    
    def baralhar(self):
        import random
        random.shuffle(self.baralho)
        
    def dar_carta(self, outra_mao, carta, x_dar = 1):
        for i in x_dar:
            outra_mao.append(carta)
            
    def reunir_cartas(self):
        for num in Carta.NUMERO:
            for naip in Carta.NAIPE:
                self.baralho += [num,naip]
        random.shuffle(self.baralho)
        
class Mao(Baralho):
    
    def __init__(self):
        self.mao = []
        
    def __str__(self):
        
        if self.mao:
            rep = ""
            for carta in self.mao:
                rep += str(carta) 
        else:
            rep += "<Sem cartas em mao...>"
            

# Teste de modulo


carta1 = Carta("A","p")
print carta1


baralho1 = Baralho()
baralho1.populate()
print baralho1

---

### Post by eightmillion on 2009-03-23
> **onnix said:**
> Greetings 

Here is a module for card game that i have been working on, it returns an __str__ error of None type, need some help:



Your problem is that you aren't returning a value from your __str__ functions so it defaults to NoneType.

This code works. Also, when you post code, use code tags, because python can be extremely hard to decipher when the indentation is stripped.
[HTML]```
code goes here.
```[/HTML]
```

# Modulo Cartas            

class Carta(object):
    """ Um baralho """

    NUMERO = ["A", "2", "3", "4", "5", "6", "7",
               "8", "9", "10", "J", "Q", "K"]   
    NAIPE = ["e","p","c","o"]                   

    def __init__(self, numero, naipe):
        self.numero = numero          
        self.naipe = naipe            

    def __str__(self):
        rep = ""      
        rep += self.numero + self.naipe
        return rep                     


class Baralho(object):
    """Um conjunto de 52 cartas."""

    def __init__(self):
        self.baralho = []

    def populate(self):
        for num in Carta.NUMERO:
            for naip in Carta.NAIPE:
                self.baralho.append(Carta(num,naip))

    def __str__(self):
        if self.baralho:
            rep = ""    
            for carta in self.baralho:
                rep += str(carta)     
            return rep                
        else:                         
            rep += "vazio"            
            return rep                

    def baralhar(self):
        import random  
        random.shuffle(self.baralho)

    def dar_carta(self, outra_mao, carta, x_dar = 1):
        for i in x_dar:                              
            outra_mao.append(carta)                  

    def reunir_cartas(self):
        for num in Carta.NUMERO:
            for naip in Carta.NAIPE:
                self.baralho += [num,naip]
                random.shuffle(self.baralho)

class Mao(Baralho):

    def __init__(self):
        self.mao = []

    def __str__(self):

        if self.mao:
            rep = ""
            for carta in self.mao:
                rep += str(carta)
            return rep
        else:
            rep += "<Sem cartas em mao...>"
            return rep

# Teste de modulo


carta1 = Carta("A","p")
print carta1


baralho1 = Baralho()
baralho1.populate()
print baralho1

```

---

### Post by onnix on 2009-03-23
Thanks a lot that's right ... Dah :p

---

