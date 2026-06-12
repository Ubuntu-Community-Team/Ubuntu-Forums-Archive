---
title: "Oja's learning rule"
date: 2015-01-27
forum: Programming Talk
---

### Post by tomasz3 on 2015-01-27
[FONT=Helvetica Neue]I'm trying to implement Oja's learning rule to my Hopfield network. I'm basing on this:[http://wiki.eyewire.org/en/Oja%27s_rule](http://wiki.eyewire.org/en/Oja%27s_rule) For now I'm trying to do like this: create base matrix of weights:[/FONT]
```
[COLOR=#00008B]def[/COLOR][COLOR=#000000] matrix_preparation[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]input_patterns[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]
    n [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] len[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]input_patterns[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000]
    num_neurons [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] len[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]input_patterns[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]0[/COLOR][COLOR=#000000]])[/COLOR][COLOR=#000000]
    weights [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] np[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]zeros[/COLOR][COLOR=#000000](([/COLOR][COLOR=#000000]num_neurons[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] num_neurons[/COLOR][COLOR=#000000]))[/COLOR][COLOR=#000000]
    [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] i [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] range[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]num_neurons[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] j [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] range[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]num_neurons[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]
            [/COLOR][COLOR=#808080]# if i == j:[/COLOR][COLOR=#000000]
            [/COLOR][COLOR=#808080]#     continue[/COLOR][COLOR=#000000]
            [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] m [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] range[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]n[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]
                weights[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]i[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] j[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]+=[/COLOR][COLOR=#000000] input_patterns[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]m[/COLOR][COLOR=#000000]][[/COLOR][COLOR=#000000]i[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000] input_patterns[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]m[/COLOR][COLOR=#000000]][[/COLOR][COLOR=#000000]j[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000]
    weights [/COLOR][COLOR=#000000]/=[/COLOR][COLOR=#000000] n
    [/COLOR][COLOR=#00008B]return[/COLOR][COLOR=#000000] weights[/COLOR]
```[FONT=Helvetica Neue]Then I use this function in Oja's training:[/FONT]
```
[COLOR=#00008B]def[/COLOR][COLOR=#000000] oja_training[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]network[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] input_patterns[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]
    [/COLOR][COLOR=#800000]"""Ucz sie&#263; metod&#261; Oja"""[/COLOR][COLOR=#000000]
    u [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] [/COLOR][COLOR=#800000]0.8[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#808080]# wspó&#322;czynnik pr&#281;dko&#347;ci uczenia[/COLOR][COLOR=#000000]

    n [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] len[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]input_patterns[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000]
    num_neurons [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] network[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]get_weights[/COLOR][COLOR=#000000]().[/COLOR][COLOR=#000000]shape[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]0[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000]
    weights [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] matrix_preparation[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]input_patterns[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000]

    [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] i [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] range[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]num_neurons[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#808080]# i do kogo wchodzi[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] j [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] range[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]num_neurons[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#808080]# j od kogo wychodzi[/COLOR][COLOR=#000000]
            [/COLOR][COLOR=#00008B]if[/COLOR][COLOR=#000000] i [/COLOR][COLOR=#000000]==[/COLOR][COLOR=#000000] j[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000]
                [/COLOR][COLOR=#00008B]continue[/COLOR][COLOR=#000000]
            [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] pattern [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] input_patterns[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000]
                V [/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000] [/COLOR][COLOR=#800000]0.0[/COLOR][COLOR=#000000]
                [/COLOR][COLOR=#00008B]for[/COLOR][COLOR=#000000] k[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] signal [/COLOR][COLOR=#00008B]in[/COLOR][COLOR=#000000] enumerate[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]pattern[/COLOR][COLOR=#000000]):[/COLOR][COLOR=#000000]
                    V [/COLOR][COLOR=#000000]+=[/COLOR][COLOR=#000000] signal [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000] weights[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]i[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] k[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000]
                weights[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]i[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] j[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]+=[/COLOR][COLOR=#000000] u [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000] V [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]pattern[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]i[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000] V [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000] weights[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]i[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] j[/COLOR][COLOR=#000000]])[/COLOR]
```[FONT=Helvetica Neue]The problem is that I'm getting: 1.Lot of NaNs if u > 0.01 2.Not working net, if u < 0.01. I mean: there is no result, blank pattern[/FONT]
[FONT=Helvetica Neue]Anyone could help me implement Oja's learning rule correctly?[/FONT]

---

### Post by ofnuts on 2015-01-28
[http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/NumericalPython/files/paper_1.pdf](http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/NumericalPython/files/paper_1.pdf)

---

### Post by lisati on 2015-01-28
> **ofnuts said:**
> [http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/NumericalPython/files/paper_1.pdf](http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/NumericalPython/files/paper_1.pdf)
Nice.

---

### Post by tomasz3 on 2015-01-28
> **ofnuts said:**
> [http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/NumericalPython/files/paper_1.pdf](http://www.ucs.cam.ac.uk/docs/course-notes/unix-courses/NumericalPython/files/paper_1.pdf)


Was rather hoping for answer: is there a problem of alghoritm or my implementation.

---

