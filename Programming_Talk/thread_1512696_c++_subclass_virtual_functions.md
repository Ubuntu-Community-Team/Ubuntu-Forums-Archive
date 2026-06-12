---
title: "c++ subclass virtual functions"
date: 2010-06-18
forum: Programming Talk
---

### Post by tbastian on 2010-06-18
I have a class "Parameter" and a subclass "ParameterCreator". At one point in my program, I create a ParameterCreator, then pass it around as a Parameter *. By the time I get around to calling methods on it, it calls the Parameter functions, not the overloaded ParameterCreator functions!

I even tried:

```
std::cout << typeid ( *parameter ) . name () << std::endl;
```

and it prints:

```
9Parameter
```

What could be happening here?

---

### Post by MadCow108 on 2010-06-18
overloaded functions which are used in polymorphic fashion must be virtual so the actual function to be called will be determined at runtime. Otherwise it will assume it will call the function of the base class.
[http://en.wikipedia.org/wiki/Virtual_function#C.2B.2B](http://en.wikipedia.org/wiki/Virtual_function#C.2B.2B)

If you do know the type at compile time you could also use a cast to the correct type.

---

### Post by tbastian on 2010-06-18
> **MadCow108 said:**
> overloaded functions which are used in polymorphic fashion must be virtual so the actual function to be called will be determined at runtime. Otherwise it will assume it will call the function of the base class.
[http://en.wikipedia.org/wiki/Virtual_function#C.2B.2B](http://en.wikipedia.org/wiki/Virtual_function#C.2B.2B)

If you do know the type at compile time you could also use a cast to the correct type.

The overloaded functions are declared as Virtual. When I do the typeid call, for some reason it comes back as the superclass, not the subclass though...

I also don't know the type at compile time.

---

### Post by MadCow108 on 2010-06-18
are you sure the overloaded functions are virtual in the base class and not only in the subclass?
Does your system have Run-time type information support?
does the same happen when you do a dynamic_cast?

can you give a minimal compilable example reproducing your problem?

---

### Post by tbastian on 2010-06-18
> **MadCow108 said:**
> are you sure the overloaded functions are virtual in the base class and not only in the subclass?
Does your system have Run-time type information support?
does the same happen when you do a dynamic_cast?

can you give a minimal compilable example reproducing your problem?

I'm working on a minimal example, but in the mean time...

I haven't tried a dynamic_cast because I'm never sure if I'm getting a Parameter, a ParameterCreater or a TimeParameter...

I'm fairly sure I have run-time type information... the following example works:

```
#include <iostream>
#include <typeinfo>

using namespace std;

class foo
{
	public:
		foo () {}
		~foo () {};
		virtual void do_stuff () { cout << "foo" << endl; }
};

class bar : public foo
{
	public:
		bar () {}
		~bar () {};
		virtual void do_stuff () { cout << "bar" << endl; }
};

class foobar
{
	public:
		foo * f;
		foobar ( foo * f )
			: f ( f )
		{}
		void do_stuff () { f -> do_stuff (); };
};

void type ( foo * f )
{
	cout << "type is: " << typeid ( *f ) . name () << endl;
}

int main ( int argc, char ** argv )
{
	bar b;
	b . do_stuff ();

	foo * f = new bar ();
	f -> do_stuff ();

	type ( &b );
	type ( f );

	foobar * fb = new foobar ( &b );
	fb -> do_stuff ();

	delete f;
	delete fb;

	return 0;
}
```

---

### Post by tbastian on 2010-06-18
So after trying very hard to make an example that breaks, I'm just going to have to give up. The software I'm working on is much to large to copy paste code to create an example (too many dependencies), so I'll just paste some of the key code snippents:

Parameter Class:
```

class Parameter
{
	/**@param param_name the name of this parameter
	 * @param type the type of data (eg f8 == 8 byte float)
	 * @param parent the packet this parameter belongs to
	 */
	Parameter ( char * param_name, data_type type, Packet * parent );
	/**Adds a value to the parameter
	 * @param value the data point to add
	 */
	void add ( double value );
...
	/**@return an Elastic array of the data
	 */
	virtual ElasticArray<double> & get_data ();
...
};

```

Parameter Creator:

```

class ParameterCreator
	: public Parameter
{
	/**constructor for add, sub, mul and div operations
	 * @param param_name
	 * @param type the type of data to be stored
	 * @param parent
	 * @param p1 param1
	 * @param p2 param2
	 * @param sampleRate1
	 * @param sampleRate2
	 * @param op operation type (eg, ADD, SUB, MUL, DIV, RESAMPLE )
	 */
	ParameterCreator ( char * param_name, data_type type, Packet * parent,
					   Parameter & p1, Parameter & p2,
					   double sampleRate1, double sampleRate2,
					   operation_t op );
...
	/**@return an Elastic array of the data
	 */
	virtual ElasticArray<double> & get_data ();
...
};

ElasticArray<double> &
ParameterCreator::get_data ()
{
	update ();
	return Parameter::get_data ();
}

void
ParameterCreator::update ()
{
	double i1, i2;

	ElasticArray<double> & data1 = param1 . get_data ();
	ElasticArray<double> & data2 = param2 . get_data ();

	for ( i1 = pos1, i2 = pos2;
		  i1 < param1 . size () && i2 < param2. size ();
		  i1 += sample_rate_1, i2 += sample_rate_2 ) {

		switch ( op ) {
			case ADD:
				add ( data1 [ (int)( i1 + 0.5 ) ] + data2 [ (int)( i2 + 0.5 ) ] );
				break;
			case SUB:
				add ( data1 [ (int)( i1 + 0.5 ) ] - data2 [ (int)( i2 + 0.5 ) ] );
				break;
			case MUL:
				add ( data1 [ (int)( i1 + 0.5 ) ] * data2 [ (int)( i2 + 0.5 ) ] );
				break;
			case DIV:
				add ( data1 [ (int)( i1 + 0.5 ) ] / data2 [ (int)( i2 + 0.5 ) ] );
				break;
			case RESAMPLE:
				add ( data1 [ (int)( i1 + 0.5 ) ] );
				break;
			default:
				break;
		}
	}

	pos1 = param1 . size ();
	pos2 = param2 . size ();
}

```

Where I initialize all of it:

```

ParameterCreator * pc = new ParameterCreator ( resample -> get_name (), F8,
filereader -> get_dataset () -> get_packet ( dataset_size - 1 ),
*resample, samplerate, RESAMPLE );

// add the resampled parameter to the dataset
filereader -> get_dataset () -> get_packet ( dataset_size - 1 ) -> add_parameter ( pc );

```

---

### Post by tbastian on 2010-06-18
Hmm, this is interesting:

```

ParameterCreator * pc = new ParameterCreator ( resample -> get_name (), F8, filereader -> get_dataset () -> get_packet ( dataset_size - 1 ), *resample, samplerate, RESAMPLE );

        // add the resampled parameter to the dataset
        filereader -> get_dataset () -> get_packet ( dataset_size - 1 ) -> add_parameter ( pc );

        // make sure we use the right resampled parameter
	if ( resample == y_parameter )
		y_parameter = pc;
	else
		param = *pc;

std::cout << typeid ( *y_parameter ) . name () << std::endl;
std::cout << typeid ( *(&param) ) . name () << std::endl;

```

Says they're both of type Parameter...
'param' is a Parameter reference... does that make a difference??

---

### Post by tbastian on 2010-06-18
Apparently it being a reference DOES matter. I just ended up making a local pointer and using that, now it works. Thanks MadCow for your time!

---

