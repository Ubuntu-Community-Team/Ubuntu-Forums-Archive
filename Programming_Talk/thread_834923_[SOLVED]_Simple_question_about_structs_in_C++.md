---
title: "[SOLVED] Simple question about structs in C++"
date: 2008-06-19
forum: Programming Talk
---

### Post by Zeotronic on 2008-06-19
C++: I have some code, and I know its not right, but how is it supposed to be?
```
struct Image_User{
	Image_User(image=NULL){
		frame=0;
		time=0;
	}
	Image_Data* image;
	unsigned long frame;
	float time;
};
```
I want to be able to just go Image_User(image);... do you get what I'm saying? How am I supposed to do that... I'm pretty sure I've done it:
```
struct Image_User{
	Image_User(Image_Data* a){
		image=a;
		frame=0;
		time=0;
	}
	Image_Data* image;
	unsigned long frame;
	float time;
};
```
I'm pretty sure I've done that before, but I'd rather do it the other way.

---

### Post by LaRoza on 2008-06-20
In C++, structs are just like classes, except everything is public by default. 

Just get any reference on classes and you have it for structs.

---

### Post by Qrikko on 2008-06-20
not JUST like classes :) but well close enough :) but you don't have some of the features which you have in classes, (such as polymorphism, multiple inheritance, and Templates, (obs not 100% sure about them, but pretty sure) (edit: bah now you made me curious and I have to spend time finding out the facts if I am just pulling "facts" out my **** here :P edit 2: but that didn't take me too long, as I understand it you are correct, struct is IDENTICAL to class except default viability, my bad)

but well that really don't have much to do with the question I guess :)

about how to do it..

you want to be able to create an instance of Image_User using a default constructor to initialize it or else put it to NULL?

I would have a constructor like this:

Image_User(Image_Data* a=NULL):image(a)
{do your ste-huff;}

(I think you are trying to use a default value and also to instantiate the member image with the value of *a)

and creating a instance:
Image_User my_stuff(image);

Please feel free to fill in more information if I missunderstand what you are trying to do :)

---

### Post by dwhitney67 on 2008-06-20
You can try something like:
[PHP]struct Image_User
{
  Image_User( Image_Data *a = 0,
              const unsigned long f = 0,
              const float t = 0.0 )
  {
    image = a;
    frame = f;
    time  = t;
  }

  Image_Data    *image;
  unsigned long  frame;
  float          time;
};[/PHP]

This way, you can instantiate an Image_User either with or without giving an Image_Data pointer.  The reason an Image_User object can be instantiated without providing any arguments is because the local function variables have been given default values.

So these are legal:
[PHP]
Image_User imageUser_1 = Image_User();
Image_User imageUser_2 = Image_User( new Image_Data() );
Image_User imageUser_3 = Image_User( new Image_Data(), 10 );
Image_User imageUser_4 = Image_User( new Image_Data(), 10, 5.5 );

Image_Data imageData_1;
Image_Data imageData_2 = new Image_Data();

Image_User imageUser_5 = Image_User( &imageData_1 );
Image_User imageUser_6 = Image_User( imageData_2 );

// Danger!... do not delete pointer, because then imageUser_6 will
// have a dangling reference to imageData_2.
delete imageData_2;
[/PHP]

Do you plan on Image_Data taking ownership of the pointer to Image_Data?  If so, I recommend that you define a destructor that will release (that is, delete) the memory allocated to it.

You might want to consider doing some research with respect to Boost's shared-pointers ([http://www.boost.org/doc/libs/1_35_0/libs/ptr_container/doc/ptr_container.html](http://www.boost.org/doc/libs/1_35_0/libs/ptr_container/doc/ptr_container.html)).

P.S.  By convention, when programming in C++, a class definition is used for complex data objects.  You are free to use a struct, however just bear in mind that if you do not explicitly classify the member data as 'private', that they are accessible by the function that instantiates the structure.  This sort of defeats to some degree the purpose of data encapsulation.

---

