---
title: "Erro de dependencias"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by Jose Ponteira on 2013-04-08
obtenho o seguinte erro no ubuntu 12.10 64 bites "Error: Opening the cache (E: Encountred a section with no Package:header, E: Problem with a Mergelist/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en, E: The package lists or status file coukd not be parsed or opened.)

Por favor como posso resolver o problema, e tirar o simbolo vermelho do canto superior direito do monitor?

Abr
José Ponteira

---

### Post by Sandertje on 2013-04-08
I'm sorry, but this is an English language forum. If you would be so kind to translate your question from Portuguese to English, someone might be able to help you :-).

---

### Post by Jose Ponteira on 2013-04-08
Sorry, here is :)



I get the following error in ubuntu 12.10 64 bites "Error: Opening the cache (E: Encountred a section with no Package: header, E: Problem with the Mergelist/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_quantal_main_i1 8n_Translation -en, E: The package lists or status file could not be parsed or opened.)

Please how can I solve the problem, and take the red symbol in the upper right corner of the monitor?

---

### Post by ibjsb4 on 2013-04-08
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo rm -r /var/lib/apt/lists/* 
sudo mkdir /var/lib/apt/lists/partial 
sudo apt-get update
```

Should fix it :)

---

### Post by Jose Ponteira on 2013-04-08
Thank you. Error fixed.

---

### Post by slickymaster on 2013-04-08
Boas, José.

Não te esqueças de marcar a tua thread como resolvida. Vê a minha assinatura se tiveres dúvidas de como o fazer.

Abraço.

---

### Post by Jose Ponteira on 2013-04-08
Please explain what the origin of this error?
What can i do to no repeat?

Sorry my english is very basic. I hope you understand.

---

### Post by Sandertje on 2013-04-08
Somehow, your a file in your var/lib/apt/lists folder got corrupted. This can happen, for instance, when your do ```
sudo apt-get update
``` while on a public wifi network (e.g. a coffee bar) which redirects all HTTP requests to some web page explaining how to get access through their network. Exactly how the file got corrupted in your case is, unfortunately, hard to tell. 

And don't worry about your English - it is understandable, and that's the important thing (we're not a forum discussing linguistics :P)

---

### Post by slickymaster on 2013-04-08
José, vê este [artigo]("http://www.maketecheasier.com/fix-ubuntu-update-errors/2011/12/16") que explica não só o que pode causar o erro que tiveste como também as soluções para a resolução dele.

Se tiveres alguma dúvida devido ao facto de estar em inglês, diz, estamos aqui para ajudar.

Abraço.

P.S.: se não tiveres mais questões, não te esqueças de fechar a thread, tal como te sugeri nos meu anterior post.

---

