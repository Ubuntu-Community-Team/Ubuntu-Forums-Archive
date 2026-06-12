---
title: "What's wrong (python)?"
date: 2011-01-28
forum: Programming Talk
---

### Post by 12332123 on 2011-01-28
I've just made my first foray into programming and after a couple of hours I've managed to put my so-far limited vocab to use making a program that gives the equation of a line from three points (and will eventually do circles too). Anyway; I would really like some help debugging.

```

x1 = input("please enter x coordinate of point a:")
y1 = input("please enter y coordinate of point a:")
x2 = input("please enter x coordinate of point b:")
y2 = input("please enter y coordinate of point b:")
x3 = input("please enter x coordinate of point c:")
y3 = input("please enter y coordinate of point c:")

def linearoutput(x1,y1,x2,y2,x3,y3):

    def grad(a,b,c,d):
        if a==c:
            grad="vertical"
        elif b==d:
            grad="horizontal"
        else:
            grad=float(b-d)/float(a-c)
        return grad

    def grad2(a,b,c,d):
        grad2=-1.0/grad(a,b,c,d)
    return grad2

    def findc(a,b,c,d):
        findc = midpoint(b,d)-(grad2(a,b,c,d)*midpoint(a,c))
    return findc


    def d():
        if grad(x1,y1,x2,y2)=="vertical" or grad(x1,y1,x2,y2)=="horizontal":
            d="N/A"
        else:
            d=findc(x1,y1,x2,y2)
        return d

    def e():
        if grad(x1,y1,x3,y3)=="vertical" or grad(x1,y1,x3,y3)=="horizontal":
            e="N/A"
        else:
            e=findc(x1,y1,x3,y3)
        return e

    c=grad(x1,y1,x2,y2)

    f=grad(x1,y1,x3,y3)
    
    if x1==x2==x3 and y1==y2==y3:

        print "Are you fucking kidding me? These three points are the exact fucking same, you retard. Go back and try again, and this time try not to fail so hard."
    
    elif x1==x2 and y1==y2 and f=="horizontal":

        print "These three points (of which a and b are spacially equivalent) describe a straight line of equation y =",y1

    elif x1==x2 and y1==y2 and f=="vertical":

        print "These three points (of which a and b are spacially equivalent) describe a straight line of equation x =",x1

    elif x1==x2 and y1==y2:
        
        print "These three points (of which a and b are spacially equivalent) describe a straight line of equation y =",f,"x +",e()

    elif x1==x3 and y1==y3 and c=="horizontal":

        print "These three points (of which a and c are spacially equivalent) describe a straight line of equation y =",y1

    elif x1==x3 and y1==y3 and c=="vertical":

        print "These three points (of which a and c are spacially equivalent) describe a straight line of equation x =",x1

    elif x1==x3 and y1==y3:
        
        print "These three points (of which a and c are spacially equivalent) describe a straight line of equation y =",c,"x +",d()

    elif x2==x3 and y2==y3 and c=="horizontal":

        print "These three points (of which b and c are spacially equivalent) describe a straight line of equation y =",y1

    elif x2==x3 and y2==y3 and c=="vertical":

        print "These three points (of which b and c are spacially equivalent) describe a straight line of equation x =",x1

    elif x2==x3 and y2==y3:
        
        print "These three points (of which b and c are spacially equivalent) describe a straight line of equation y =",c,"x +",d()
        
    elif c=="horizontal":

        print "These three points describe a straight line of equation y =",y1

    elif c=="vertical":

        print "These three points describe a straight line of equation y =",y1

    else:
         
        print "These three points describe a straight line of equation y =",c,"x +",d()
        return linearoutput

def grad(a,b,c,d):
    if a==c:
        grad="vertical"
    elif b==d:
        grad="horizontal"
    else:
        grad=float(b-d)/float(a-c)
    return grad

if (x1==x2 and y1==y2) or (x2==x3 and y2==y3) or (x1==x3 and y1==y3) or grad(x1,y1,x2,y2)==grad(x2,y2,x3,y3) :
    print linearoutput(x1,x1,y1,y2,x3,y3)

```

---

### Post by Vaphell on 2011-01-28
what is the problem exactly?
btw that if x1==x2==x3 and y1==y2==y3: line is comedic gold :D

---

### Post by 12332123 on 2011-01-28
Don't worry, I managed to get it fixed. (Needless to say there were many errors). Thanks for the feedback on my amazing comedy skills .

---

### Post by tgm4883 on 2011-01-28
Right here

```
    def grad2(a,b,c,d):
        grad2=-1.0/grad(a,b,c,d)
    return grad2

    def findc(a,b,c,d):
        findc = midpoint(b,d)-(grad2(a,b,c,d)*midpoint(a,c))
    return findc
```

your return lines aren't indented. Should be

```
    def grad2(a,b,c,d):
        grad2=-1.0/grad(a,b,c,d)
        return grad2

    def findc(a,b,c,d):
        findc = midpoint(b,d)-(grad2(a,b,c,d)*midpoint(a,c))
        return findc
```

Also doesn't appear to midpoint defined anywhere

:EDIT: 

NM, looks like you got it fixed

---

### Post by squenson on 2011-01-28
To define a line you only need two distinct points, so what is happening if the three points are not aligned?

---

