---
title: "Can't pass float into Max/MSP object, C problem"
date: 2010-10-27
forum: Programming Talk
---

### Post by themusicalduck on 2010-10-27
I'm not sure if there are many here who have some experience programming objects for Max/MSP, but I'm hoping that this is more of a general programming problem.

For some reason when I pass a float into an object programmed in C, the float is either saved as 0.0, 2.0 or some random long string of numbers. I get no errors or warnings when I build the object and very little happens to the float along the way, so I can't figure out why it won't receive it properly.

I'll post the relevant code and then the entire code in separate tags.

```
void save_lengths(t_variables *x, float length_in)
{
	float new_length;
	float value_saved = x->value;
		
	post("length_in = %f", length_in);
					
	new_length = value_saved * length_in;
 		
	atom_setfloat(&x->music_lengths[x->index], new_length);
	
	x->index++;
	
	post("saved new value %f", x->music_lengths[x->index]);
}
```

The post function is like printf but it prints it to Max/MSP. It's at the point that the value is displayed as something random, so literally nothing is done to the float before being printed.

```
class_addmethod(c, (method)save_lengths, "lengths_in", A_FLOAT, 0);
```

This is the line that registers how the float is passed to the object. A message from Max/MSP "lengths_in 1.0" is sent to the object and the value should be saved as length_in in the function.

I've been doing this in the exact same way with integers, and it works absolutely fine.

I'm really hoping this is some simple thing I'm missing. I'm assuming it must be possible to do such a thing as use a float instead of int.

Here is the code in its entirety -

```
#include "uwemax.h"
#include "unistd.h"
#include "stdio.h"
#include "math.h"

typedef struct 
	{
		t_object u_ob;
		void *lengths_out;
		t_atom music_lengths[100];
		int index;
		float value;
		int tempo;
		int piece_array_size;
		float length;
		
	} t_variables;

void *new(void);
void registermessages(t_class *c);
void init(t_variables *x);
void save_lengths(t_variables *x, float length_in);
void save_tempo(t_variables *x, int tempo);
void output_new_values(t_variables *x);
void set_piece_length(t_variables *x, int piece_length);


void *class;

int main(void)
{	
	t_class *c;
	c = class_new(MAXOBJECT_NAME, 
				  (method)new, 0, 
				  (long)sizeof(t_variables), 0, 
				  0);
	registermessages(c);
	class_register(gensym("box"), c);
	class = c;				
	return 0;
}

void *new(void)
{	
	t_variables *x = 0;
	if (x = (t_variables *)object_alloc(class)) 
	{
		x->lengths_out = outlet_new(x, 0);
		init(x);
	}
	return (x);
}


void registermessages(t_class *c)
{
	class_addmethod(c, (method)save_tempo, "new_tempo", A_LONG, 0);
	class_addmethod(c, (method)save_lengths, "lengths_in", A_FLOAT, 0);
	class_addmethod(c, (method)output_new_values, "done", 0);
	class_addmethod(c, (method)set_piece_length, "piece_length", A_LONG, 0);


}

void init(t_variables *x)
{
	int index;
	for (index = 0; index < 100; index++)
	{
		atom_setlong(&x->music_lengths[index], 0.0);
	}
	post("loaded");
}

void set_piece_length(t_variables *x, int piece_length)
{
	x->piece_array_size = piece_length;
	post("saved");
}

void save_tempo(t_variables *x, int tempo)
{	
	x->value = (60.0/tempo) * 1000.0;

	post("saved");
	post("crotchet = %f", x->value);	
}

void save_lengths(t_variables *x, float length_in)
{
	float new_length;
	float value_saved = x->value;
	
	post("value_saved = %f", value_saved);
	
	post("length_in = %f", length_in);
					
	new_length = value_saved * length_in;
 	
	post("length = %f", new_length);
	
	atom_setfloat(&x->music_lengths[x->index], new_length);
	
	x->index++;
	
	post("saved new value %f", x->music_lengths[x->index]);
	
	
}

void output_new_values(t_variables *x)
{
	int index;	
	
	for (index = 0; index < x->piece_array_size; index++)
	{
		outlet_atoms(x->lengths_out, 1, &x->music_lengths[index]);
	}
	
	
	for (index = 0; index < 100; index++)
	{
		atom_setfloat(&x->music_lengths[index],  0.0);
	}
	
	x->index = 0;
	
	post("done");
}

```

---

### Post by Arndt on 2010-10-27
> **themusicalduck said:**
> I'm not sure if there are many here who have some experience programming objects for Max/MSP, but I'm hoping that this is more of a general programming problem.

For some reason when I pass a float into an object programmed in C, the float is either saved as 0.0, 2.0 or some random long string of numbers. I get no errors or warnings when I build the object and very little happens to the float along the way, so I can't figure out why it won't receive it properly.


I don't know anything about Max/MSP, but I would try the same thing with the 'double' type and see what happens.

---

### Post by themusicalduck on 2010-10-27
Hooray! Thankyou very much, it works perfectly now.

Cheers. :guitar:

---

