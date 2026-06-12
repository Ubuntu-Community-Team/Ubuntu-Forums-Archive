---
title: "iterate through list python"
date: 2007-12-24
forum: Programming Talk
---

### Post by bradleyd on 2007-12-24
hello everyone,

I am having trouble trying to iterate through a list of images. I basically have a image viewer in Gtk(yes I know there are plenty of image viewers:))On the toolbar I have open,back, and next. When you click on open you pick a directory, and through os.walk it populates a list with images. What I want to do is when you hit next it will goto the next image in the list. I have tried iter() but it only loads the next image and wont keep going through the list. Here is ther function that populates the list:
```
def get_chapters(self,name):
		self.FILES = []
		for root, dirs, files in os.walk(name):
			for i in files:
				k = os.path.join(root,i)
				if k.endswith(".jpg"):
					self.FILES.append(k)
		self.FILES.sort()
		self.textview.set_from_file(self.FILES[0])
		self.textview.show()
```
thanks for your time,
Brad

---

### Post by engla on 2007-12-24
Once you have the images in 'self.FILES', get the iterator once with iter(), then use that iterator's next method to get the next image.

Normally to iterate through a list you simply do (of course):
```
for image in self.FILES:
    # use image
```

Here you would do
```
imageiter = iter(self.FILES)
first = imageiter.next()
while # Something:
    # Do long computations here
    # get next item
    try:
         nextimg = imageiter.next()
    except StopIteration:
        break
    # use nextimg
```
Something like that what was I thought you wanted to do

---

### Post by bradleyd on 2007-12-24
thanks for the respond. I tried what you said but it jumps to the third image but thats it(if you click it again nothing happens). In the temp image folder there are three images. When the app starts, there is no image shown. As soon as you click open and pick the temp image folder the first image is shown.The next button on the toolbar is bound to a function called next. It looks like this:
```
def next(self,action):
		imageiter = iter(self.FILES)
		first = imageiter.next()
		while 1:
		# Do long computations here
		# get next item
			try:
				nextimg = imageiter.next()
				self.textview.set_from_file(nextimg)
				self.textview.show()
			except StopIteration:
				break
```
not really sure why it jumps to the third image?
thanks again

---

### Post by bradleyd on 2007-12-25
just to try something I wanted to see what nextimg was, so I added print statement:
```
while 1:
		# Do long computations here
		# get next item
			try:
				nextimg = imageiter.next()
				print nextimg
				self.textview.set_from_file(nextimg)
				self.textview.show()
			except StopIteration:
				break
```
it is returning 
> 
/home/tmp/image/image2
/home/tmp/image/image3
Instead of just image2

---

### Post by Wybiral on 2007-12-25
Every time you need to increment, you call the "next()" method on the iterator returned by "iter()". "next()" will throw an exception after it reaches the last element. The code above is to iterate over all of them (which is why it keeps going past the second one).

---

### Post by bradleyd on 2007-12-25
could you give an example,I do not know if I understand you correctly

---

### Post by Martin Witte on 2007-12-25
to get a list of files matching some pattern the glob module might be what you need, see eg:

[PHP]>>> import os
>>> print os.listdir("F:\Pictures\Dusseldorf") # sorry, I'm writing from my windows box
['Dusseldorf0115.JPG', 'Dusseldorf0116.JPG', 'Dusseldorf0117.JPG', 'Dusseldorf0118.JPG', 'Dusseldorf0119.JPG', 'Thumbs.db']
>>> import glob
>>> print glob.glob(r"F:\Pictures\Dusseldorf\*.[Jj][Pp][Gg]")
['F:\\Pictures\\Dusseldorf\\Dusseldorf0115.JPG', 'F:\\Pictures\\Dusseldorf\\Dusseldorf0116.JPG', 'F:\\Pictures\\Dusseldorf\\Dusseldorf0117.JPG', 'F:\\Pictures\\Dusseldorf\\Dusseldorf0118.JPG', 'F:\\Pictures\\Dusseldorf\\Dusseldorf0119.JPG']
>>> import os.path
>>> for pic in glob.glob(r"F:\Pictures\Dusseldorf\*.[Jj][Pp][Gg]"):
    print os.path.basename(pic)

Dusseldorf0115.JPG
Dusseldorf0116.JPG
Dusseldorf0117.JPG
Dusseldorf0118.JPG
Dusseldorf0119.JPG[/PHP]

---

### Post by bradleyd on 2007-12-25
thanks Martin, but I already have the images in a list and can loop through them. I am trying to use a back and next button to cycle through the pictures being displayed in the frame.
thanks again.

---

### Post by Wybiral on 2007-12-25
> **bradleyd said:**
> could you give an example,I do not know if I understand you correctly

"iter()" returns an iterator. This iterator has only one method, which is "next()". Calling "next()" will return the current value and increment the iteration. When "next()" reaches the end of the iteration, it throws an exception, "StopIteration".

```

lst = [1, 2, 3, 4, 5]

itr = iter(lst)

print itr.next()
print itr.next()
print itr.next()
print itr.next()
print itr.next()

print itr.next()

```

The last call to the "next()" method throws the exception, this can be handled using try/except.

```

lst = [1, 2, 3, 4, 5]

itr = iter(lst)

while True:
    try:
        print itr.next()
    except StopIteration:
        break

```

I suggest you read [this]("http://docs.python.org/lib/typeiter.html").

---

### Post by engla on 2007-12-25
> **bradleyd said:**
> thanks for the respond. I tried what you said but it jumps to the third image but thats it(if you click it again nothing happens). In the temp image folder there are three images. When the app starts, there is no image shown. As soon as you click open and pick the temp image folder the first image is shown.The next button on the toolbar is bound to a function called next. It looks like this:
```
def next(self,action):
		imageiter = iter(self.FILES)
		first = imageiter.next()
		while 1:
		# Do long computations here
		# get next item
			try:
				nextimg = imageiter.next()
				self.textview.set_from_file(nextimg)
				self.textview.show()
			except StopIteration:
				break
```
not really sure why it jumps to the third image?
thanks again
You have a loop over all items there, but "Next" really only want to get the next image! No wonder it jumps to the last image, you loop until you have gone through all the items and the third is the last one..

---

