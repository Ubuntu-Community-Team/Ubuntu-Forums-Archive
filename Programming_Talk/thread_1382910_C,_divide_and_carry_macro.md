---
title: "C, divide and carry macro"
date: 2010-01-16
forum: Programming Talk
---

### Post by mcweaver1 on 2010-01-16
Hi,

I am trying to write a macro which performs a divide and carry.  I have been given a macro which performs a multiply and carry:

```

# define LIMB_MAC(r1 ,r0 ,e ,f ,g , h)     \ (1)
{                                          \ (2)
   DWORD t0 =      ( DWORD )( e );         \ (3)
         t0 = t0 * ( DWORD )( f );         \ (4)
         t0 = t0 + ( DWORD )( g );         \ (5)
         t0 = t0 + ( DWORD )( h );         \ (6)
                                           \ (7)
   r0 = ( WORD )( t0                    ); \ (8)
   r1 = ( WORD )( t0 >> BITSOF ( WORD ) ); \ (9)
}

```

where, for x/y: 
r1 = the carry out
r0 = the result
e  = each bit of x (dealt with in turn in a for loop)
f  = each bit of y (     "              "           )
g  = each bit of the temporary array (currently filled with 0s) used to hold the result
h  = the carry in

To write my own macro I need to be able to understand what is happening here.  Could someone please explain it to me what goes on in lines 5, 6, and 9?

Thanks in advance.

---

