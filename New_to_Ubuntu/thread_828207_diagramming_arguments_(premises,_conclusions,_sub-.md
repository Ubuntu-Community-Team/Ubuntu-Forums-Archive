---
title: "diagramming arguments (premises, conclusions, sub-arguments). What's best program?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by hanzj on 2008-06-13
Hello, 
We're taking a Critical Thinking class.
We have learned how to visually analyze arguments by putting them in simple diagram form. I uploaded 3 basic types of diagrams that I would be making. Arguments could be a combination of one or more of these 3. We could therefore end up with sub-arguments, where a conclusion for one set of premises also serves as a premise for another conclusion. Please see attached 2 files for examples of the 3 basic types of argument.

In whatever program I use, I want the text box to widen up and get bigger when I type more and shrink when I delete text. I want that I don't have to space out boxes from each other. I don't want to have to place arrows manually. I want that things would
work out simply. 
Basically, all I as the human user want to do is to add the content of the argument, and not worry about sizing boxes and lengthening arrows and spacing between the premises and conclusions.

---

### Post by dca on 2008-06-13
I picked up the part 'diagramming' but then you lost me on everything past that...
 
In Synaptic, there's an application called 'dia'.  You can try that, I guess?

---

### Post by hanzj on 2008-06-13
I have tried Dia.

While looking at the file, refer to the examples below:
Type 1: Convergent Argument (V-Diagram)
P1: Fred is successful in his career.
P2: Fred has a secure and supportive marriage
P3: Fred hand a secure and stable childhood
C: Therefore, Fred is a happy person.


In this sort of argument, the premises operate independently of each other. If one of the premises in a Convergent or V argument is missing or false, the remaining ones still provide support for the conclusion.
They are called V arguments because the lines joining the premises to the conclusion form a V (when the premises number 2).

----------------------------------------------

Type 2: Linked Argument (T diagram)
P1: Every physically handicapped person who has tried to find employment knows the anguish of rejection.
P2: Laurence is physically handicapped.
P3. Laurence has tried to find employment.
C: Therefore, Laurence knows the anguish of rejection.

Note that each premise, by itself, provides little or no support for the conclusion. The premises have to work together. If one premise is wrong or missing, then the set of premises fails. All premises have to work together to reach the conclusion.

---------------------------------------------

Type 3 Argument: Serial Argument

P1: Lisa was born in the USA to American parents.
P2: This means that Lisa is an American citizen.
C: Therefore: Lisa can vote in the elections.

Note that P2 serves as the conclusion for P1. Note also that P2 serves as the premise for C. The above is really 2 arguments in one. The P1-P2 set is a sub-argument for C.


Hope this makes things clear.

---

### Post by paulderol on 2008-06-13
Freemind can be used to create flowcharts, brainstorming maps, and other methods of linking independent thoughts visually and across multiple sets of criteria. 
[http://freemind.sourceforge.net/wiki/index.php/Main_Page]("http://freemind.sourceforge.net/wiki/index.php/Main_Page")

i think this is EXACTLY what you are looking for, fellow worker.

---

### Post by Hospadar on 2008-06-13
ew diagrams =P
If you must make them, though, I've used dia before with success.  It's nice and simple and I like it for that reason.  Most of the other diagram drawers I've seen (umbrello and argoUML for example) are more targeted towards UML.  I'm sure there are some other good ones out there aside from dia

---

### Post by hanzj on 2008-06-13
Paulderol,
I've also installed FreeMind, too. And I use FreeMind for my other work. But FreeMind doesn't seem to be the right fit for visually reconstructing arguments.
If you can upload a mindmap that you've created for each of the 3 basic types of arguments, maybe I will see what you're saying.

---

### Post by hanzj on 2008-06-13
Hospadar,
I know that Dia can help me reach the goal. But you and I know that even a program like Gimp can do it, too. Please know that what I'm looking for is a tool where I do NOT Have to mess around with tweaking stuff. I want ONLY to input my text.  The issue before me is NOT "what program can do this" but rather "What program is suited for this".


Please upload some examples

---

### Post by KingTermite on 2008-06-13
> **paulderol said:**
> Freemind can be used to create flowcharts, brainstorming maps, and other methods of linking independent thoughts visually and across multiple sets of criteria. 
[http://freemind.sourceforge.net/wiki/index.php/Main_Page]("http://freemind.sourceforge.net/wiki/index.php/Main_Page")

i think this is EXACTLY what you are looking for, fellow worker.

From what you are describing, I agree with paulderol. Freemind is probably the exact type of tool you are looking for. It's basically designed as a way to "diagram your thoughts and ideas".

---

### Post by hanzj on 2008-06-13
But I need my argument reconstruction not in a free-flowing web. But from Top to Bottom with ways to distinguish linked arguments from convergent arguments.
I've used FreeMind a bit for other work. I don't know if FreeMind can do what my uploaded files can. Please show me by example upload or by direction.

---

### Post by unutbu on 2008-06-13
```
sudo apt-get install graphviz
```

Save this as V.dot:

```
digraph V {
node [shape=box]
P1 -> C
P2 -> C
P3 -> C
}
```

Save this as T.dot

```
digraph T {
node [shape=box]
P1 -> a1 [arrowhead=none] 
P2 -> a2 [arrowhead=none] 
P3 -> a3 [arrowhead=none] 
{a1 a3} -> a2 [arrowhead=none] 
{rank=same; a1 a2 a3}
a2 -> C
a1 [label="" shape=plaintext height=0 width=0]
a2 [label="" shape=plaintext height=0 width=0]
a3 [label="" shape=plaintext height=0 width=0]
}
```

Save this as S.dot

```
digraph serial {
node [shape=box]
P1 -> P2 -> C
}
```

Run it like this (change the 'gq' in 'viewer=gq' to whatever you use to view png):
```
file=V; viewer=gq; dot -Gratio=auto -Tpng -o $file.png $file.dot && $viewer $file.png
file=T; viewer=gq; dot -Gratio=auto -Tpng -o $file.png $file.dot && $viewer $file.png
file=S; viewer=gq; dot -Gratio=auto -Tpng -o $file.png $file.dot && $viewer $file.png
```


I only learned about graphviz yesterday, so there may be a better way to do the T diagram than how I did it.

---

### Post by paulderol on 2008-06-13
you're right, good sir, freemind only really makes that happen if you start with the conclusion as the parent node, and it does require tweaking to achieve the visual effects that you want. 

*just curiously he asks if there were any programs that actually DO do this in any OS?*

---

### Post by hanzj on 2008-06-13
Unutbu,
I'm not a coder. If I install graphviz, do I have to do coding?

---

### Post by The Cosmic Hobo on 2008-06-13
This all looks pretty nifty.
FreeMind, in particular, seems useful. I use Inspiration (on Windows) at the moment for the same task, and it really helped with my dissertation.

---

### Post by unutbu on 2008-06-14
hanzj, I think the simplest way for you to decide if graphviz could work for you is to try it. If you end up not liking it, it's easy to un-install:

```
sudo apt-get purge graphviz
sudo apt-get autoremove

```


Using graphviz would require you to "code" in a language of sorts, but it is a pretty simple language. 

Look at S.dot and V.dot. You can probably understand the language immediately!

T.dot is not that complicated either. All you need to know is that 

```
P1 -> a1 [arrowhead=none] means don't draw an arrow between node P1 and a1.

{a1 a3} -> a2 means draw an arrow between a1 -> a2 and a3 -> a2.

{rank=same; a1 a2 a3} means put a1, a2 and a3 on the same line.

a1 [label="" shape=plaintext height=0 width=0] means don't use a label, don't draw a shape around the label, and make the node as small as possible -- so the node a1 is essentially invisible.
```

If you remove most of the bracketed options from T.dot like this:
```

digraph T2 {
node [shape=box]
P1 -> a1
P2 -> a2
P3 -> a3
{a1 a3} -> a2
{rank=same; a1 a2 a3}
a2 -> C
}
```
and then run 
```

file=T2; viewer=gq; dot -Gratio=auto -Tpng -o $file.png $file.dot && $viewer $file.png
```

you'd end up with the diagram below (see attached). Imagine a1, a2 and a3 being smaller and invisible, and you end up with the T diagram you wanted. 

If you choose to try graphviz, type

```
man dot
```
and read the man page which explains the graph file language. 

If you run into any problems, post here and I'll try to help.

---

### Post by hanzj on 2008-07-09
@unutbu,
Thanks for sharing your code for Graphviz. Is there a way to save your code as some sort of "template" so that we can, in future work, proceed directly to the content of the argument, and skip out on the task of coding?

---

### Post by unutbu on 2008-07-09
Are you thinking of a little program that will say
ask if you want a V,T,or S diagram, and then prompt you for P1,P2,P3 and C, and then pop out the png file?

---

### Post by hanzj on 2008-07-09
@unutbu,
Yes, I think so. But the program should allow for depth, too. By depth, I mean nested arguments ("sub-arguments"). 


And it doesn't have to be a PNG file or any type of graphic file for that matter.

---

### Post by unutbu on 2008-07-09
hanzj, I've tried to write a program that would give you a simple way to enter arbitrary S,T,V nested diagrams... and failed. I am finding that as the diagram grows in complexity I have to resort to  more tricks to force the diagram to have straight edges and the positioning I want. And in fact, in the end, I don't know enough tricks to get it looking right (see attached. I can't seem to bring P14 and P15 closer without dot (graphviz) dumping core.)

I am beginning to suspect that graphviz is not a good tool for the problem you pose. (Or that I don't know enough to wield graphviz properly). 

My apologies for leading you down this blind alley.

---

### Post by hanzj on 2008-07-09
unutbu,
thank you so much for your efforts. I think our time on this was fruitful. This is what science is about, isn't it? Doing experiments and seeing whether one's hypothesis is validated. So we've learned today (that we didn't learn before) that perhaps graphvis is not the right tool.

I guess the market for what I'm asking for is small. There are not a lot of philosophers out there in the world, and high-tech ones at that. 8-)

---

### Post by hanzj on 2008-07-09
unutbu,
on second thought, perhaps it's too early to give up. Just an idea: is there a way to get graphviz to automatically raise a row (P10-P15) if there's not enough space underneath to form straight arrows?

---

### Post by hanzj on 2008-07-09
actually, I might be able to use your coding. I'm going to use it just for my own use, and won't be showing it to anybody else. And I don't mind some curviness in the lines. I just hope that when the "Px" is replaced with a regular English sentence, that it would look as nice as your last png file.

---

### Post by unutbu on 2008-07-09
This is perhaps a little better, though not perfect (P15 is too far from P14).

The problem is, I used special weighting for certain links, and I don't know how to write a program which can predict a priori what weightings are required to produce the desired diagram. My method was iterative: I would produce a diagram, see that two nodes were too close or too far apart and then alter the weighting of the edge accordingly.

---

### Post by hanzj on 2008-07-10
unutbu,
Wow. thanks for your efforts.

---

### Post by unutbu on 2008-07-11
I've written a little program that can make S,T,V nested diagrams. All you have to do is write a template -- something like

```
T(S(A("Place"),A("your"),A("text")),A("between"),A("the"),A("quotation marks"))
```

Two problems:
(1) The program works for small diagrams, but for more complicated diagrams the lines start to curve and you get some pretty funky pictures. (See the attachments)
(2) You'll need to install python-pyparsing, which takes about 2MB of space.
```

sudo apt-get install python-pyparsing
```

If you don't like it, you can remove the package with
```

sudo apt-get purge python-pyparsing
sudo apt-get autoclean
```

To use the program:
Save this in a file called make-diagram.py:
```

#!/usr/bin/python

import sys
import re
import os
from pyparsing import Forward, Literal, SkipTo

def uniquify(path):
    num=0
    newpath=path
    (pathpart,ext)=os.path.splitext(path)
    while os.path.isdir(newpath) or os.path.isfile(newpath):
	newpath=pathpart+'-'+str(num)+ext
	num+=1
    return newpath

       
def dotty_edge(obj1,obj2,options=''):
    if not (obj1 and obj2):
        print "report_edge called without two nodes/diagrams"
        sys.exit()
    result="%s -> %s %s\n"%(obj1.out_name,obj2.in_name,options)
    return result


term = Forward()
lparen = Literal("(").suppress()
rparen = Literal(")").suppress()
iterm = "I" + lparen + rparen
aterm = "A" + lparen + '"' + SkipTo('"') + '"' + rparen
sterm = "S" + lparen + term + ',' + term + ','+ term + rparen
tterm = "T" + lparen + term + ',' + term + ','+ term + ',' + term + rparen
vterm = "V" + lparen + term + ',' + term + ','+ term + ',' + term + rparen
term << (aterm | iterm | sterm | tterm | vterm )


def parse(a_list):
    """ parse takes a list and returns a Diag and the rest of the list if any. 
        A_Diag is text
        I_Diag is an invisible node
        """
    the_type = a_list[0]
    i=1
    if the_type == 'I':
        diag=I_Diag()
#        print "I_Diag created"
        return (diag,a_list[i:])
    if the_type == 'A':
        if not a_list[i] == '"':
            print "There should be a quotation mark here: %s"%("".join(a_list)[:10])
            sys.exit()
        the_content=''
        i+=1
        while True:
            token = a_list[i]
            if not token == '"':
                the_content+=token
                i+=1
            else:
                break
        diag=A_Diag(content=the_content)
        return (diag,a_list[i+2:])
    elif the_type == 'S':
        diag=S_Diag()        
        (subdiag,b_list)=parse(a_list[i:])
        diag.content.append(subdiag)
        diag.in_name=subdiag.in_name
        (subdiag,b_list)=parse(b_list)        
        diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)
        diag.content.append(subdiag)
        diag.out_name=subdiag.out_name
        return (diag,b_list)
    elif the_type == 'T':
        diag=T_Diag()
        (subdiag,b_list)=parse(a_list[i:])
        diag.in_name=subdiag.in_name
        diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)        
        diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)
        diag.content.append(subdiag)
        for i in range(3):
            (subdiag,c_list)=parse("I()")
            diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)
        diag.content.append(subdiag)
        diag.out_name=subdiag.out_name
        return (diag,b_list)
    elif the_type == 'V':
        diag=V_Diag()
        (subdiag,b_list)=parse(a_list[i:])
        diag.in_name=subdiag.in_name 
        diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)        
        diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)
        diag.content.append(subdiag)
        (subdiag,b_list)=parse(b_list)
        diag.content.append(subdiag)
        diag.out_name=subdiag.out_name 
        return (diag,b_list)
    else:
        print "Can't parse %s"%("".join(a_list))
        sys.exit()
    
idx=0
# print globals()
# print globals()['idx']
class Diag(object):
    def __init__(self):
#        print "Creating node%s"%globals()['idx']
        self.in_name="node%s"%globals()['idx']
        self.out_name="node%s"%globals()['idx']        
        globals()['idx']+=1

class I_Diag(Diag):
    def __init__(self):
        Diag.__init__(self)

    def dotty(self):
        return '%s [ label="" shape=plaintext height=0 width=0 ]'%self.in_name+"\n"
        
class A_Diag(Diag):
    def __init__(self,content=''):
        Diag.__init__(self)
        self.content=content   

    def dotty(self):
        return r'%s [ label="%s" ]'%(self.in_name,self.content)+"\n"

class S_Diag(Diag):
    def __init__(self):
        Diag.__init__(self)
        self.content=[]
        
    def dotty(self):
        result="".join(self.content[i].dotty() for i in range(3))
        result+=dotty_edge(self.content[0],self.content[1],'[ weight=50 ]')
        result+=dotty_edge(self.content[1],self.content[2],'[ weight=50 ]')
        return result

class T_Diag(Diag):
    def __init__(self):
        Diag.__init__(self)
        self.content=[]
        
    def dotty(self):
        """
        P1   P2   P3             0   1   2
        P4   P5   P6             3   4   5
             P7                      6
        (P1, ..., P7)  =  (self.content[0], ..., self.content[6])
        """
        result="".join(self.content[i].dotty() for i in range(7))
# Make P1, P2, P3 appear on the same row
#        result+="{rank=same; %s %s %s}\n"%tuple([self.content[i].out_name for i in range(3)])
# Make the invisible P4, P5, P6 appear on the same row
        result+="{rank=same; %s %s %s}\n"%tuple([self.content[i+3].out_name for i in range(3)])
# Draw the edges
        result+=dotty_edge(self.content[0],self.content[3],'[ arrowhead=none ]')
        result+=dotty_edge(self.content[1],self.content[4],'[ arrowhead=none ]')
        result+=dotty_edge(self.content[2],self.content[5],'[ arrowhead=none ]')
        result+=dotty_edge(self.content[3],self.content[4],'[ arrowhead=none ]')
        result+=dotty_edge(self.content[5],self.content[4],'[ arrowhead=none ]')
        result+=dotty_edge(self.content[4],self.content[6],'')

# Strengthen the bond between the P1 -> P7, P2 -> P7, P3 -> P7.
#         result+=dotty_edge(self.content[0],self.content[6],'[ style="invis" weight=10 ]')
#         result+=dotty_edge(self.content[1],self.content[6],'[ style="invis" weight=20 ]')
#         result+=dotty_edge(self.content[2],self.content[6],'[ style="invis" weight=10 ]')
# Strengthen the bond between the P4 -> P7, P5 -> P7, P6 -> P7.
#         result+=dotty_edge(self.content[3],self.content[6],'[ style="invis" weight=10 ]')
#         result+=dotty_edge(self.content[4],self.content[6],'[ style="invis" weight=20 ]')
#         result+=dotty_edge(self.content[5],self.content[6],'[ style="invis" weight=10 ]')

# Strengthen the bond between P1, P2, P3        
#        result+='%s -> %s -> %s [ style="invis" weight=10 ]'%tuple([self.content[i].in_name for i in range(3)])+"\n"
# Strengthen the bond between the 3 invisible nodes P4, P5, P6
#        result+='%s -> %s -> %s [ style="invis" weight=10 ]'%tuple([self.content[i+3].in_name for i in range(3)])+"\n" 
        return result

class V_Diag(Diag):    
    def __init__(self):
        Diag.__init__(self)
        self.content=[]
        
    def dotty(self):
        result="".join(self.content[i].dotty() for i in range(4))
        option='[ weight=10 samehead="%s" ]'%self.out_name
        noarrow_option='[ weight=0 samehead="%s" arrowhead=none ]'%self.out_name
        result+=dotty_edge(self.content[0],self.content[3],noarrow_option)
        result+=dotty_edge(self.content[1],self.content[3],option)
        result+=dotty_edge(self.content[2],self.content[3],noarrow_option)
        result+="{rank=same; %s %s %s}\n"%tuple([self.content[i].out_name for i in range(3)])
        result+='%s -> %s -> %s [ style="invis" weight=0 ]'%tuple([self.content[i].out_name for i in range(3)])+"\n" 
        return result

if __name__ == '__main__':
    
    from optparse import OptionParser
    parser = OptionParser()
    parser.add_option("-f", "--file", metavar="FILE", dest="filename",
                      default="diagram.txt",
                      help="read FILE (default=diagram)")
    try:
        (opt, args) = parser.parse_args()
    except:
        parser.print_help()
        sys.exit()

    basename=os.path.splitext(opt.filename)[0]
    
    try:
        sock=open(opt.filename,"r")
    except:
        print "Could not find file %s"%opt.filename
        parser.print_help()
        sys.exit()
        
    text=sock.read()
    sock.close()

#    print "text=%s"%text
    text_list=text.split("\n")
    for line in text_list:
        if line.startswith('#') or not line:
            print line
            continue
        print "Parsing %s"%line

        outfile=uniquify(basename+".dot")
        pngfile=uniquify(os.path.splitext(outfile)[0]+".png")
        
        a_list=term.parseString(line)
#        print a_list
        (diag,b_list)=parse(a_list)
        out_text=diag.dotty()

        print "Creating %s..."%outfile
        sock=open(outfile,"w")
        sock.write("digraph DIAGRAM {\nnode [shape=box]\n")
        sock.write(out_text)
        sock.write("}")
        sock.close()
        cmd="dot -Gratio=auto -Tpng -o %s %s && **gqview **%s"%(pngfile,outfile,pngfile)
        print "Running %s..."%cmd
        os.system(cmd)
    
```

Near the bottom of the program, change gqview to whatever image viewer you use.

Make it executable:

```
chmod 755 make-diagram.py
```

Save this in a file called diagram.txt:

```

# Testing S diagram
S(A("To be forewarned is to be forearmed"),A("To be four-armed is very odd"),A("It is very odd to be forewarned"))
#S(S(A("P1"),A("P2"),A("P3")),S(A("P4"),A("P5"),A("P6")),S(A("P7"),A("P8"),A("P9")))

# Testing V diagram
V(A("The shoe is on the other foot"),A("It's hard to walk with two left feet"),A("Two feet to the left is Harry"),A("It is impossible to walk barefoot\nwith Harry unless he gives you\nback your shoe.")) 

# Testing T diagram
T(A("Big Mama is\nin the house"),A("Elvis has left\nthe building"),A("A house is\na building"),A("Big Mama is\nnot Elvis"))

#Testing nested diagrams

#T(S(A("C"),A("D"),A("F")),A("C"),A("D"),A("F"))

T(A("strawberry"),V(A("banana"),A("lemon"),A("cream"),A("sugar")),A("blend"),A("Mmmm"))

#T(A("E"),T(A("P1"),A("P2"),A("P3"),A("C")),A("D"),A("F"))

T(S(A("P1"),A("P2"),A("P3")),V(A("P4"),A("P5"),A("P6"),A("P7")),A("P8"),A("P9"))

#T(T(T(A("P10"),A("P11"),A("P12"),A("P1")),T(A("P13"),A("P14"),A("P15"),A("P2")),V(A("P16"),A("P17"),A("P18"),A("P3")),A("C")),T(S(A("P19"),A("P20"),A("P4")),A("P5"),A("P6"),A("D")),T(A("P7"),A("P8"),A("P9"),A("E")),A("F"))

T(A("E"),T(A("P7"),A("P8"),A("P9"),T(T(A("P10"),A("P11"),A("P12"),A("P1")),T(A("P13"),A("P14"),A("P15"),A("P2")),V(A("P16"),A("P17"),A("P18"),A("P3")),A("C"))),T(S(A("P19"),A("P20"),A("P4")),A("P5"),A("P6"),A("D")),A("F"))

```
diagram.txt is an example of the kind of templates you will have to write. Lines begining with # are ignored. If you "uncomment" those lines by removing the #, you'll see a few more examples.

To run the program type:

```
./make-diagram.py 
```
or 
```

./make-diagram.py --file path/to/template/file

```
If the template file is called "roger", then the image files will be called roger.png or roger-[num].png.

---

### Post by hanzj on 2008-07-11
Ununtbu:
Your first two attached png files cracked me up! ha ha.

---

### Post by hanzj on 2008-07-11
Diagram.txt is something I have to write every time I create a new diagram? You mean I have to add some coding in my text? For example

"T(T(T(A("P10"),A("P11"),A("P1)"

As opposed to just writing something like

P1
P2
P3
?

---

### Post by unutbu on 2008-07-11
Yes. You have to specify that you want a T diagram rather than a V or an S.

The A("text") syntax is something I can fix -- hopefully shortly -- to just "text". (I'm still learning python and pyparsing.)

So except for the A's and the parentheses, the diagram language is about as minimal as it can possibly get.

If you have a different idea for how you would like to enter the diagrams, explain it to me and I'll see if I can redo the parser to accomodate.

For example, we could do reverse polish notation

P1
P2
P3
P4
T

... Reverse polish is definitely as minimal as it gets. It's also very easy to implement.

By the way, the syntax for S,T,V diagram is
```

S( subdiagram, subdiagram, subdiagram )

T( subdiagram, subdiagram, subdiagram, subdiagram )

V( subdiagram, subdiagram, subdiagram, subdiagram )

A( "text" )

```

Each of these strings above is itself a subdiagram.

---

### Post by jjoensuu on 2008-08-13
Another interesting diagramming software, also written in Java (and with a GNU license) is Carneades.

More info about Carneades can be found at:
[http://carneades.berlios.de/]("http://carneades.berlios.de/")

---

### Post by hanzj on 2008-08-13
jjoensu, thanks for telling us about carneades.

---

