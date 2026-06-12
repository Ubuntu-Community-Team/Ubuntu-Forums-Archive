---
title: "[QT4/python]probleme de transmission de donnees"
date: 2008-04-30
forum: Programming Talk
---

### Post by tsic on 2008-04-30
Bonjour,
Mon code serveur/multiclient fonctionnait parfaitement avant que je l'integre dans l'interface QT4 mais après C'est le desastre totale. J'etais obligée d'eliminer les thread et de mettre un simple client et malgrès ça:
L'interface QT4 (de serveur que j'ai faite) contenant un editText et lineText un bouton envoyer: permettant le transfert de donnees entre un serveur un des clients(executé par dos).
Le programme est réalisé à l'aide de python2.5.
Le probleme est lorsque j'execute le programme l'interface ce bloque (après l'appuie sur le bouton connexion) .
J'ai cherché mais j'ai pas trouvé la solution.

voici le code:
```

    def chat(self):
       
        rep = self.chates.text()
        self.envoies.append("Donnees Envoyees>"+rep)     
        self.chates.clear()             
        return rep
     
    def conec(self):
        HOST = self.adripes.text()
        PORT = int(self.nipes.text())
       
        mySocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
       
        try:
            mySocket.bind((HOST, PORT))
        except socket.error:
            self.envoies.setText("La liaison du socket a l'adresse choisie a echoue.")
            sys.exit()
        while 1:
            self.envoies.append("Serveur pret en attente de requetes .")
            mySocket.listen(5)   
            connexion, adresse = mySocket.accept()
            c= time.strftime('%A %c')
            client= "Connexion au port" + str(adresse[1]) + "  a " + c
            self.envoies.append(client)
            donneesRecues = connexion.recv(8192)
            t=time.strftime("%H:%M:%S")
            self.envoies.append(" Donnees Recues " +t+ " > "+ donneesRecues)
            rep = self.chat()
            connexion.send(rep)


```

Quand j'ai cherché sur internet j'ai trouvé qu'il existe des Qthread mais  j'ai pas su ni comment les utilisées ni à quoi servent.
Merci

---

### Post by tseliot on 2008-04-30
I know that this section of the forum reports this:
> **Programming Talk**
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any language is allowed. 

However it means that any **programming** language is allowed. Your posts should be in English.

---

### Post by nvteighen on 2008-04-30
> **tseliot said:**
> I know that this section of the forum reports this:


However it means that any **programming** language is allowed. Your posts should be in English.
Then, why not change that header? It's absolutely ambiguous!

His problem is that the GUI gets blocked after pressing the button to connect to the server. (No, I don't know French. I've just applied Comparative Linguistics from Spanish and Italian)

---

### Post by tseliot on 2008-04-30
> **nvteighen said:**
> Then, why not change that header? It's absolutely ambiguous!
I have reported the problem to the admins.

---

### Post by LaRoza on 2008-04-30
> **nvteighen said:**
> Then, why not change that header? It's absolutely ambiguous!



This is the first time it has come up.

---

### Post by LaRoza on 2008-04-30
> **nvteighen said:**
> His problem is that the GUI gets blocked after pressing the button to connect to the server. (No, I don't know French. I've just applied Comparative Linguistics from Spanish and Italian)

That is normal. Without threading, the program run sequentially.

The GUI should run on a different thread.

---

### Post by nvteighen on 2008-04-30
> **LaRoza said:**
> This is the first time it has come up.
[PHP]
#include <stdio.h>
int main(void)
{
 puts("Hi there!, this is a post written in C!");
 puts("Hey, don't blame me: any language is allowed!");
 
 return 0;
}
[/PHP]

I know, bad programming joke. But I couldn't resist.

---

### Post by LaRoza on 2008-04-30
> **nvteighen said:**
> [PHP]
#include <stdio.h>
int main(void)
{
 puts("Hi there!, this is a post written in C!");
 puts("Hey, don't blame me: any language is allowed!");
 
 return 0;
}
[/PHP]

I know, bad programming joke. But I couldn't resist.

Gehen Sie weg!

---

### Post by nvteighen on 2008-04-30
> **LaRoza said:**
> Gehen Sie weg!
:p

---

### Post by tsic on 2008-04-30
#-o I'm really sorry. I forget about the langage.
So I said:

Hello,

My code server/multiclient functioned perfectly before I integred it into the interface QT4 but after,it's the total disaster. I was obliged to eliminate the thread and to put a simple client code and dispite:the interface QT4 (of server which I made) containing a editText and lineText a button to send: allowing the transfer of data between a server and many clients(executed by DOS). The program is realized with python2.5.
And not C++!!!!


The problem is when I execute the program the interface blocks (after I press on the button connection). I tryed to modify but I didn't find the solution.


when I searched in the internet I found some of Qthread...
I didn't understand how to use them or what are their utilities.

thank u

---

### Post by Kadrus on 2008-04-30
Bonjour,essaye de trouver une solution pour ton probleme aux Ubuntu Forums Francaise,[http://ubuntu-fr.org/](http://ubuntu-fr.org/) etre ca t'aidera plus dans une communaute francophone..bonne chance ^_^

---

