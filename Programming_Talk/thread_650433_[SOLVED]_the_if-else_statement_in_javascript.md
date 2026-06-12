---
title: "[SOLVED] the if-else statement in javascript"
date: 2007-12-26
forum: Programming Talk
---

### Post by fyplinux on 2007-12-26
I am using javascript in building my VRML world. I found something strange.

Java script is strange that if there is an if –else, both if and else would be sanned over, if the value swithes in the if statement.

e.g.

A = true;
If(A){
  A = false;
}
Else{
 A =true;
}

//both if and else would be executed.
my original code in vrml is:
```

if(filledA == false){  //not filled
	child[0] = new SFNode('Transform {
	translation -5 0 0
	children[ Shape {
		geometry Box {
			size 10 10 10
		}
		appearance Appearance {
			material Material {	//green box at x = -5
				diffuseColor .04 .62 0
				specularColor .41 1 .36
				ambientIntensity .04
				shininess .12
			}

		}
	}

	]
}
');
filledA = true;
}
else{//filled
	child[0] = new SFNode('Transform {
	translation 5 0 0
	children[ Shape {
		geometry Box {
			size 10 10 10
		}
		appearance Appearance {
			material Material {//blue box at x = 5
				diffuseColor .34 .22 1
				specularColor .51 1 .16
				ambientIntensity .04
				shininess .52
			}

		}
	}

	]
}
');
filledA = false;
}

//both the green box and the blue box showed up.

```

---

### Post by Majorix on 2007-12-26
It might be a problem with your browser. Tried with different browsers already?

---

### Post by fyplinux on 2007-12-26
> **Majorix said:**
> It might be a problem with your browser. Tried with different browsers already?

I only have one browser currently.

I also think it might be not the problem of javascript, but the problem of my code. or the limitation of VRML

---

