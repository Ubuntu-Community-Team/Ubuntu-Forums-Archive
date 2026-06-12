---
title: "Quick Python Question"
date: 2006-01-27
forum: Programming Talk
---

### Post by flummoxed on 2006-01-27
I'm learning python, and I'm trying to make a simple program to tell you the slope. I just can't figure out how to get variables from one function to work in another function. Don't you use the return statement so it stores the variable and you can use it outside of the function?
```

def theSlope (x1, y1, x2, y2):
	slope = (y2-y1)/(x2-x1)
	return slope
def theIntercept (x1, y1, x2, y2):
	theSlope (0, 20, 30, 80)
	x = 3
	y = 2
	b = slope * x
	intercept = y - b
	print intercept
        return intercept
theIntercept (0, 20, 30, 80)

```

I'm just using x = 3 and y = 2 as temporary variables for the purpose of developing the code. This program won't really be that useful, as I'm just writing it as an exercise to get more familiar with python. Anyways, how do I get the value from theSlope to use in theIntercept? There are probably some other problems in the code, but I can figure them out later. All I'm concerned with is the variable.

Thanks. :)

---

### Post by engla on 2006-01-27
As seen in C, Java and elsewhere, the function metaphor is like this

```
result = function(arguments)
```

So you are forgetting that variables and names inside one function have nothing to do with the ones in another.
What you need to do in theIntercept is to make your slope line something like this:
```

slope = theSlope(1,2,3,4)
```

Now the variable 'slope' holds the result returned from the function theSlope.

---

### Post by flummoxed on 2006-01-27
Thank you, that makes sense. Program works now! :)

---

