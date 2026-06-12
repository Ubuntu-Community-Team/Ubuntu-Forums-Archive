---
title: "ensure that sizeof ( double ) == 8?"
date: 2011-06-13
forum: Programming Talk
---

### Post by tbastian on 2011-06-13
Is there a way I can guarantee that the size of my double is 8? I know theres a stdint.h library for various integer types, but I need a guarantee that my double is 8 bytes long, regardless of the platform!

Edit: by 'platform' I mean compiler to compiler on different machines, as opposed to operating system. This will be run on linux.

---

### Post by NovaAesa on 2011-06-13
There's no way to guarantee that a double will be 8 bytes long. However, you could use a typedef that is set differently depending on the target platform.

---

### Post by Npl on 2011-06-13
sizeof doesnt return the size in bytes, but in chars. so if chars have 16 bit then sizeof(double) == 4, yet doubles can still have 64 bit

so you should be testing for CHAR_BIT == 8 (defined in limits.h) and properties of doubles (defined in float.h) instead. there is no way to address smaller elements than char`s in C, so alot things will break if you expect to access bytes. But this is pretty much a pathological case that you wont ever encounter.

---

### Post by trent.josephsen on 2011-06-13
> **tbastian said:**
> Is there a way I can guarantee that the size of my double is 8? I know theres a stdint.h library for various integer types, but I need a guarantee that my double is 8 bytes long, regardless of the platform!

No, you probably don't.  Why would you want that?

What you might want is a guarantee that any floating-point number with a given number of decimal digits can be rounded into a floating-point number and back again without changing the value of those digits, in which case you want to look at DECIMAL_DIG and its friends FLT_DIG, DBL_DIG, and LDBL_DIG (defined in <float.h>).

What you also might want is a guarantee that you can store a very large positive number, such as 10^50, or a very small one, such as 10^-50, into a given floating-point type.  In that case, you want to examine the <TYPE>_MIN and <TYPE>_MAX macros, also defined in <float.h>.

Another thing you might want is some measure of representable accuracy for a given type, which is probably <TYPE>_EPSILON, again defined in <float.h>.

What none of these things will do for you is enforce compliance.  If your compiler doesn't support 64-bit floating-point numbers (as I suppose you actually want), nothing you can do (well, short of implementing your own floating-point engine) will make it otherwise, and the best you can do is #error out before compilation proper begins.

The correct solution is the one that doesn't depend on arbitrary assumptions about the implementation or operating environment.

@Npl: The C Standard uses "byte" exclusively as a measure of the size of a "char".  However, you're right that bytes can have sizes other than 8.

---

### Post by tbastian on 2011-06-13
I am reading UDP packets from an inertial navigation system (INS), and the specification says '8 byte double' as the datatype for some data packets.

---

### Post by simeon87 on 2011-06-13
> **tbastian said:**
> I am reading UDP packets from an inertial navigation system (INS), and the specification says '8 byte double' as the datatype for some data packets.

That doesn't mean you need to store doubles as 8 bytes. You need to take care of the fact that your platform might store them with more or less bytes but the given data will always have 8 bytes. So you read a double of 8 bytes, you check the size of doubles on your platform, and you perform the necessary conversion / storing to get the data. Most of the time a double will be 8 bytes though.

---

### Post by tbastian on 2011-06-13
> **simeon87 said:**
> That doesn't mean you need to store doubles as 8 bytes. You need to take care of the fact that your platform might store them with more or less bytes but the given data will always have 8 bytes. So you read a double of 8 bytes, you check the size of doubles on your platform, and you perform the necessary conversion / storing to get the data. Most of the time a double will be 8 bytes though.

I know that, but the easiest way to do this is create a the following structure:

```

#pragma pack ( 1 )
typedef struct {
	uint32_t	week;			// week number since midnight Jan 5, 1980
	double 		seconds;		// seconds since sunday morning
	double		lat;			// degrees
	double		lon;
	double		height;
	double		north_vel;		// m/s
	double		east_vel;
	double		vert_vel;
	double		roll;			// degrees
	double		pitch;
	double		heading;
	uint32_t	status;			// bits
	uint32_t	crc;
} inspvas_t;
#pragma pack ()

```

then memcpy the packet I get to this structure. I think I'll just leave it for now and worry about it when I run into issues. Maybe put in a line somehwere such as:

```

assert ( sizeof ( double ) == 8 )

```

---

### Post by stchman on 2011-06-13
> **tbastian said:**
> Is there a way I can guarantee that the size of  my double is 8? I know theres a stdint.h library for various integer  types, but I need a guarantee that my double is 8 bytes long, regardless  of the platform!

Edit: by 'platform' I mean compiler to compiler on different machines,  as opposed to operating system. This will be run on linux.

I believe it is widely accepted that a double is 8 bytes long.

A short is 2 bytes and a char is 1 byte.  The float, int, and long are compiler dependent IIRC.

```

#include <stdio.h>

int main( void ) {
    printf( "%d\n", sizeof( double ) );
    printf( "%d\n", sizeof( float ) );
    printf( "%d\n", sizeof( int ) );
    printf( "%d\n", sizeof( long  ) );
    printf( "%d\n", sizeof( short ) );
    printf( "%d\n", sizeof( char ) );
    
    return 0;
}


```

---

### Post by NovaAesa on 2011-06-13
> **stchman said:**
> I believe it is widely accepted that a double is 8 bytes long.

A short is 2 bytes and a char is 1 byte.  The float, int, and long are compiler dependent IIRC.
This will be generally true on the vast majority desktop and server machines. However, there are lots of microcontrollers out there that do funny things with floating point numbers such as have float = double = 4 bytes, or have no floating point numbers at all.

---

### Post by trent.josephsen on 2011-06-14
Simply verifying that two interpretations of "double" have the same size won't guarantee binary compatibility.  Endianness comes to mind, but it's also possible (although pretty unlikely) that the protocol you're dealing with uses a different internal representation than IEC 60559 (which C99 requires, and most C89 implementations probably use).

MAKE NO ASSUMPTIONS.  It's probably the primary rule of C programming.

---

### Post by tbastian on 2011-06-14
> **trent.josephsen said:**
> MAKE NO ASSUMPTIONS.  It's probably the primary rule of C programming.

I will definitely check that the code is compatible with the machine it will likely run on, and I'm fairly certain that the endianness of both machines are the same, but I've got it all ready to do byte swapping just in case.

Thank you everybody for your responses

---

