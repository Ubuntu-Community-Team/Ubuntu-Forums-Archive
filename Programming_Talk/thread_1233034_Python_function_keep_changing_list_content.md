---
title: "Python function keep changing list content"
date: 2009-08-06
forum: Programming Talk
---

### Post by LinuxQ on 2009-08-06
Hello all,

I'm new to python and I'm having problems with the following:

```
def cross_over(spec1, spec2, func_set):
	x = choose_random_element(spec1)
	y = choose_random_element(spec2)
	x_value = return_element(spec1, x)
	y_value = return_element(spec2, y)
	spec3 = spec1[:]
	if x_value in func_set.keys() and y_value in func_set.keys():
		print 'a'
		exec('spec3' + str(return_indices(x[0:-1])) + ' =  spec2' + str(return_indices(y[0:-1])))
	elif y_value in func_set.keys() and x_value not in func_set.keys():
		print 'b'
		exec('spec3' + str(return_indices(x)) + ' = spec2' + str(return_indices(y[0:-1])))
	elif y_value not in func_set.keys() and x_value in func_set.keys():
		print 'c'
		exec('spec3' + str(return_indices(x[0:-1])) + ' = spec2' + str(return_indices(y)))
	else:
		print 'd'
		exec('spec3' + str(return_indices(x)) + ' = spec2' + str(return_indices(y)))
	if type(spec3) is not list:
		spec3 = [spec3]	
	if type(spec3) is list and len(spec3) == 1 and type(spec3[0]) == list:
		spec3 = spec3[0]
	return spec3
	
def choose_random_element(expr):
	if isinstance(expr, list) and len(expr) > 1:
		elm = random.choice(range(len(expr)))
		index = [elm]
		if isinstance(expr[elm], list) and len(expr[elm]) > 1:
			index += [choose_random_element(expr[elm])]
		return list(flatten(index))
	else:
		return 0
	
def return_element(expr, index):
	if type(expr) is not list:
		expr = [expr]
	if isinstance(index, list):
		index_str = ''
		for i in index:
			index_str += '[' + str(i) + ']'
		return eval('expr' + index_str)
	else:
		return expr[0]
	
def return_indices(index):
	index_str = ''
	if type(index) is not list:
		index = [index]
	for i in index:
		index_str += '[' + str(i) + ']'
	return index_str
		
def flatten(lst):
	for elem in lst:
		if type(elem) in (tuple, list):
			for i in flatten(elem):
				yield i
		else:
			yield elem

func_set = {'add':2, 'sub':2, 'mul':2, 'div': 2}
x = ['add', ['add', 'x', 'x'], ['sub', -4, 0]]
y = ['add', ['add', 'x', 'x'], ['sub', -4, 0]]
z = cross_over(x, y,func_set)

```

so after calling cross_over() it changes the content of the input lists.  I've tried everything but the problem still persists, any ideas why is that?

Sorry for the long code but I couldn't put it in simpler terms.

Thanks in advance

---

### Post by unutbu on 2009-08-06
Given the way choose_random_element is defined, it looks like spec1 and spec2 may be lists of lists. 
[PHP]
spec3 = spec1[:]
[/PHP]
only copies the top level of the lists. The "deeper" parts of the list are references to the same objects. So altering the list inside of the list in spec3 will alter spec1.

That might happen here:
[PHP]
spec3 = spec3[0]
[/PHP]
Perhaps try
[PHP]
import copy

spec3 = copy.deepcopy(spec1)[/PHP]

---

### Post by LinuxQ on 2009-08-06
Thanks man, it worked.  You just saved my life :D

---

