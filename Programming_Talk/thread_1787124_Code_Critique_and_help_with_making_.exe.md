---
title: "Code Critique and help with making .exe"
date: 2011-06-20
forum: Programming Talk
---

### Post by Neezer on 2011-06-20
Hi,

I have a program that I wrote in python. I'm looking for some constructive criticism and some help on making it into an executable file for windows.

anyways, the program creates a 16 character password and outputs it to a window on the screen. It also allows you to create many passwords by pressing a 'generate' button in the window.

```

#!/usr/bin/python
# pwgen.py
# This program will create a 16 character password using lowercase letters,
# uppercase letters, numbers, and symbols. You can then copy and paste the
# password into any appliction to have a random and secure password.


from Tkinter import *
from random import *
 
def random_password():
  charlist = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o',
              'p','q','r','s','t','u','v','w','x','y','z','A','B','C','D',
              'E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S',
              'T','U','V','W','X','Y','Z','0','1','2','3','4','5','6','7',
              '8','9','!','@','#','$','%','^','&','*','(',')','_','-','=',
              '+',',','<','.','>','?','/']
  pw = ''
  length = 16
  for i in range (length):
    num = randint(0,len(charlist)-1)
    pw = pw + charlist[num]
  return pw
 
#
# BEGIN GUI CODE
#
 
root = Tk()
root.title("Password Generator")
root.resizable(0,0)
root.minsize(300,0)
 
frame = Frame(root)
frame.pack(pady=10, padx=5)
 
content = StringVar()
updater = lambda:content.set(random_password())
 
gen_btn = Button(frame, text="Generate", command=updater)
gen_btn.config(font=("sans-serif", 14),  bg="#92CC92")
gen_btn.pack(side=LEFT, padx=5)
 
field = Entry(frame, textvariable=content)
field.config(fg='blue', font=('courier',  16, "bold"), justify='center')
field.pack(fill=BOTH, side=RIGHT, padx=5)
 
root.mainloop()

```


any input would be greatly appreciated.

---

### Post by nzjethro on 2011-06-20
Hi there. Looks like a useful programme. A few pieces of advice:

1) How about including an option to generate passwords of different length? I'm sure it wouldn't be too hard to include a dropdown menu where you choose your password length. The reason I say this is because while I could probably handle 8-10 random characters, I can't remember 16 random characters, and to be honest I don't really want want to for a trivial password. Also, some websites and other password-requiring software specifies the length of password yo need (e.g. my uni website requires an 8 digit login). By having this option, you might increase your target audience.

2) On a related note, you could look into (maybe version 2) having conditions for your passwords (e.g. must have at least one letter, one number, and one symbol). Again, this is a requirement for some passwords. While probabilistically you can expect this to be the case with 16 characters, and if the conditions aren't satisfied you could easily generate a new password, it may help the professionalism of the programme if this option exists.

3) Python is a fantastic language, very easily implemented, and perfect for these kinds of programmes. However, if you are wanting to make the files executable for Windows, Python may not be the best option. If you distribute Python code to Windows, many Windows users will need Python installed on their computers, which may cause some compatibility issues. While Python is standard on all Ubuntu machines (and maybe all Linux machines), there isn't that level of acceptance in the Windows community.

Other than that, the programme looks cool, and from what I can see having played with it for a couple of minutes, seems to work well.

Try [this]("http://logix4u.net/Python/Tutorials/How_to_create_Windows_executable_exe_from_Python_script.html") guide to make a .exe.

---

### Post by slavik on 2011-06-20
[http://lmgtfy.com/?q=password+generator](http://lmgtfy.com/?q=password+generator)

:)

---

### Post by TwoEars on 2011-06-20
Now, there are a few points I'd like to bring up.

Because charlist is defined inside the function random_password, the entire list is reloaded each time the function is called. Using dis, I can show you this - 
```
>>> dis.dis(random_password)
  2           0 LOAD_CONST               1 ('a')
              3 LOAD_CONST               2 ('b')
              6 LOAD_CONST               3 ('c')
              9 LOAD_CONST               4 ('d')
             12 LOAD_CONST               5 ('e')
             15 LOAD_CONST               6 ('f')
             18 LOAD_CONST               7 ('g')
             21 LOAD_CONST               8 ('h')
             24 LOAD_CONST               9 ('i')
             27 LOAD_CONST              10 ('j')
             30 LOAD_CONST              11 ('k')
             33 LOAD_CONST              12 ('l')
             36 LOAD_CONST              13 ('m')
             39 LOAD_CONST              14 ('n')
             42 LOAD_CONST              15 ('o')

  3          45 LOAD_CONST              16 ('p')
             48 LOAD_CONST              17 ('q')
             51 LOAD_CONST              18 ('r')
             54 LOAD_CONST              19 ('s')
             57 LOAD_CONST              20 ('t')
             60 LOAD_CONST              21 ('u')
             63 LOAD_CONST              22 ('v')
             66 LOAD_CONST              23 ('w')
             69 LOAD_CONST              24 ('x')
             72 LOAD_CONST              25 ('y')
             75 LOAD_CONST              26 ('z')
             78 LOAD_CONST              27 ('A')
             81 LOAD_CONST              28 ('B')
             84 LOAD_CONST              29 ('C')
             87 LOAD_CONST              30 ('D')

  4          90 LOAD_CONST              31 ('E')
             93 LOAD_CONST              32 ('F')
             96 LOAD_CONST              33 ('G')
             99 LOAD_CONST              34 ('H')
            102 LOAD_CONST              35 ('I')
            105 LOAD_CONST              36 ('J')
            108 LOAD_CONST              37 ('K')
            111 LOAD_CONST              38 ('L')
            114 LOAD_CONST              39 ('M')
            117 LOAD_CONST              40 ('N')
            120 LOAD_CONST              41 ('O')
            123 LOAD_CONST              42 ('P')
            126 LOAD_CONST              43 ('Q')
            129 LOAD_CONST              44 ('R')
            132 LOAD_CONST              45 ('S')

  5         135 LOAD_CONST              46 ('T')
            138 LOAD_CONST              47 ('U')
            141 LOAD_CONST              48 ('V')
            144 LOAD_CONST              49 ('W')
            147 LOAD_CONST              50 ('X')
            150 LOAD_CONST              51 ('Y')
            153 LOAD_CONST              52 ('Z')
            156 LOAD_CONST              53 ('0')
            159 LOAD_CONST              54 ('1')
            162 LOAD_CONST              55 ('2')
            165 LOAD_CONST              56 ('3')
            168 LOAD_CONST              57 ('4')
            171 LOAD_CONST              58 ('5')
            174 LOAD_CONST              59 ('6')
            177 LOAD_CONST              60 ('7')

  6         180 LOAD_CONST              61 ('8')
            183 LOAD_CONST              62 ('9')
            186 LOAD_CONST              63 ('!')
            189 LOAD_CONST              64 ('@')
            192 LOAD_CONST              65 ('#')
            195 LOAD_CONST              66 ('$')
            198 LOAD_CONST              67 ('%')
            201 LOAD_CONST              68 ('^')
            204 LOAD_CONST              69 ('&')
            207 LOAD_CONST              70 ('*')
            210 LOAD_CONST              71 ('(')
            213 LOAD_CONST              72 (')')
            216 LOAD_CONST              73 ('_')
            219 LOAD_CONST              74 ('-')
            222 LOAD_CONST              75 ('=')

  7         225 LOAD_CONST              76 ('+')
            228 LOAD_CONST              77 (',')
            231 LOAD_CONST              78 ('<')
            234 LOAD_CONST              79 ('.')
            237 LOAD_CONST              80 ('>')
            240 LOAD_CONST              81 ('?')
            243 LOAD_CONST              82 ('/')
            246 BUILD_LIST              82
            249 STORE_FAST               0 (charlist)

  8         252 LOAD_CONST              83 ('')
            255 STORE_FAST               1 (pw)

  9         258 LOAD_CONST              84 (16)
            261 STORE_FAST               2 (length)

 10         264 SETUP_LOOP              59 (to 326)
            267 LOAD_GLOBAL              0 (range)
            270 LOAD_FAST                2 (length)
            273 CALL_FUNCTION            1
            276 GET_ITER
        >>  277 FOR_ITER                45 (to 325)
            280 STORE_FAST               3 (i)

 11         283 LOAD_GLOBAL              1 (randint)
            286 LOAD_CONST              85 (0)
            289 LOAD_GLOBAL              2 (len)
            292 LOAD_FAST                0 (charlist)
            295 CALL_FUNCTION            1
            298 LOAD_CONST              86 (1)
            301 BINARY_SUBTRACT
            302 CALL_FUNCTION            2
            305 STORE_FAST               4 (num)

 12         308 LOAD_FAST                1 (pw)
            311 LOAD_FAST                0 (charlist)
            314 LOAD_FAST                4 (num)
            317 BINARY_SUBSCR
            318 BINARY_ADD
            319 STORE_FAST               1 (pw)
            322 JUMP_ABSOLUTE          277
        >>  325 POP_BLOCK

 13     >>  326 LOAD_FAST                1 (pw)
            329 RETURN_VALUE

```

All the code from 0 to 249 is loaded again for no reason each time. Move it outside of the function, and pass it as a variable, as I can imagine that a charlist is something that can be changed.

Now, Python comes with some wonderful built in modules. One of which is string.

For reference, there are several things from there you could use instead of typing it all out yourself - 

```

DATA
    ascii_letters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
    ascii_lowercase = 'abcdefghijklmnopqrstuvwxyz'
    ascii_uppercase = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    digits = '0123456789'
    hexdigits = '0123456789abcdefABCDEF'
    letters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
    lowercase = 'abcdefghijklmnopqrstuvwxyz'
    octdigits = '01234567'
    printable = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTU...
    punctuation = '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
    uppercase = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    whitespace = '\t\n\x0b\x0c\r '
>>> string.printable
'0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~ \t\n\r\x0b\x0c'

```

Hope this helps.

---

### Post by Neezer on 2011-06-20
nzjethro,

Thanks for the input. I tried that link and was having some problems....I'm thinking it could be because I am trying it on my windows machine....I might have to move this over to my ubuntu machine and try again....

I got the GUI code from a different site, so it isn't mine....I am learning about tkinter though. I think adding a drop down for length would be a great feature though. I will work on it.


TwoEars,

looks like it might be worth it to add together the letters, digits, and punctuation strings to get my charlist. And then add some functionality to decide which ones you want to have. I have a site that does not allow punctuation, only numbers and letters. So that would be cool too. Also, I see what you mean about creating that list every time the function is called. It isn't much time, but it is a waste if you are going to generate more than one password.

Thanks for the input and everything. I'll post back again when I get a newer version. Python is fun for scripting this kind of stuff too. Just wish it were easier to make a .exe with python.

---

### Post by Neezer on 2011-06-21
Well, here is some added functionality!

I created a dropdown box for password length from 6 to 16 characters. It does a simple error check for the drop down value. If you don't change it, it uses a default value of 16. otherwise it seems to work quite well.

I also moved the definition of charlist out of the generate_password function. I didn't pass charlist to the function though. Is that a problem?

```

#!/usr/bin/python
# pwgen_V1.1.py
# This program will create a 16 character password using lowercase letters,
# uppercase letters, numbers, and symbols. You can then copy and paste the
# password into any appliction to have a random and secure password.

# For V1.1 changed charlist to strings added together instead of defining
# the list by typing in all the options.
# moved the charlist definition outside of the function random_password so
# that it isnt recreated every time the funciton is called.



from Tkinter import *
from random import *
import string

charlist = string.ascii_letters + string.digits + string.punctuation


#charlist = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o',
#              'p','q','r','s','t','u','v','w','x','y','z','A','B','C','D',
#              'E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S',
#              'T','U','V','W','X','Y','Z','0','1','2','3','4','5','6','7',
#              '8','9','!','@','#','$','%','^','&','*','(',')','_','-','=',
#              '+',',','<','.','>','?','/']

def random_password():
  
  pw = ''
  try:
    length = var.get()
  except ValueError:
    print 'No length of password selected. Using 16 characters by default'
    length = 16
  for i in range (length):
    num = randint(0,len(charlist)-1)
    pw = pw + charlist[num]
  return pw

def print_it(event):
    print var.get()
 
#
# BEGIN GUI CODE
#
 
root = Tk()
root.title("Password Generator")
root.resizable(0,0)
root.minsize(300,0)
 
frame = Frame(root)
frame.pack(pady=10, padx=5)
 
content = StringVar()
updater = lambda:content.set(random_password())
 
gen_btn = Button(frame, text="Generate", command=updater)
gen_btn.config(font=("sans-serif", 14),  bg="#92CC92")
gen_btn.pack(side=LEFT, padx=5)
 
field = Entry(frame, textvariable=content)
field.config(fg='blue', font=('courier',  16, "bold"), justify='center')
field.pack(fill=BOTH, side=RIGHT, padx=5)

 
var = IntVar()
var.set("Password Length")
OptionMenu(root, var, 6,7,8,9,10,11,12,13,14,15,16).pack(side=LEFT, padx=8)
 
root.mainloop()

```

---

