---
title: "[Ubuntu 12.04LTS] Segmentation Fault (Cryptography)"
date: 2014-03-23
forum: Programming Talk
---

### Post by lucas15 on 2014-03-23
Hi , i'm developing this sourcecode (Crypt method & developed by Bugsy) , but i get Segmentation Fault. I'm new with this errors and the only thing i found is "I need more memory" but i don't know how to fix.

Source code is here.

NOTE: The idea of the program is run it from ubuntu terminal , like 

```
~/Desktop/crypt/crypt --k "###" --s "Hi members of ubuntuforums"
```

```

#include <stdio.h>
#include <string.h>


void CryptString( char *szString , unsigned int iSize , const char *szKey )
{
        if( !iSize )
            return;


        const char *szTmpKey = szKey;


        while( iSize-- )
        {
            *szString = *szString++ ^ *szKey++;


            if( !*szKey )
                szKey = szTmpKey;
        }
}




int main( int argc, char* args[] )
{
    argc = 5;


    if( ( argc - 1 ) == 4 )
    {
        args[0] = "hi bitches";
        args[1] = "--key";
        args[2] = "2";
        args[3] = "--string";
        args[4] = "1";


        int iKey = 0 , iString = 0, i;


        for( i = 0 ; i < 5; i++ )
        {
            if( iKey != 0 && iString != 0 )
                break;


            if ( strcmp(args[i], "--k") == 0 || strcmp(args[ i ], "-key") == 0)
            {
                iKey = i;
            }
            if ( strcmp(args[ i ],"--s") == 0 || strcmp(args[ i ],"--string") == 0)
            {
                iString = i;
            }
        }


        if( iKey = 0 || iString == 0 )
        {
            printf( "No se encontraron los parámetros correspondientes\n" );
            printf( "[ --k , -key ] - [ --s , -string ] \n" );
        }
        else
        {


             int ilen = strlen( args[ iString + 1 ] );
            printf( "==========================\n" );
            printf( "Key = %s\n" , args[ iKey + 2 ] );
            printf( "Texto ingresado = -%s- \n", args[ iString + 1 ] );
            CryptString( args[ iString + 1 ] , ilen, args[ iKey + 2 ] );
            printf( "Texto saliente =  -%s- \n" , args[ iString + 1 ] );
            printf( "==========================\n" );
        }


    }
    else
    {
        printf( "4 (Cuatro) parámetros requeridos! \n" );
        printf( "[ --k , -key ] - [ --s , -string ] \n" );
    }


}

```

---

### Post by spjackson on 2014-03-24
I think your crash is down to one of two faults, or possibly a combination.

1. You may be trying to overwrite the string literal "2" here:
```

            *szString = *szString++ ^ *szKey++;



```
2. The above is only true if this line of code does what you want it to. What it actually does is undefined.
```

gcc -o crash -g crash.c -Wall

crash.c: In function CryptString:
crash.c:16: warning: operation on szString may be undefined
crash.c: In function main:
crash.c:61: warning: suggest parentheses around assignment used as truth value
crash.c:88: warning: control reaches end of non-void function

```

So, don't amend args (traditionally labelled argv). Copy it and amend the copy. Don't increment szString on the above line; increment it separately on the next line.

---

### Post by lucas15 on 2014-03-24
Do you mean do something like this ? NOTE: I'm completly noob with C , i have only basic data about proggraming this.

```

#include <stdio.h>
#include <string.h>




void CryptString( char *szString , unsigned int iSize , const char *szKey )
{
    	if( !iSize )
            return;


    	const char *szTmpKey = szKey;


    	while( iSize-- )
    	{
    	    *szString++;
    	    *szKey++;


    	    *szString = *szString ^ *szKey;
            //*szString = *szString++ ^ *szKey++;


            if( !*szKey )
                szKey = szTmpKey;


        }
}




int main( int argc, char* args[] )
{
    argc = 5;


	if( ( argc - 1 ) == 4 )
	{
        args[0] = "hi bitches";
	    args[1] = "--key";
	    args[2] = "2";
	    args[3] = "--string";
	    args[4] = "1";


        int iKey = 0 , iString = 0, i;


		for( i = 0 ; i < 5; i++ )
		{
			if( iKey != 0 && iString != 0 )
				break;


			if ( strcmp(args[i], "--k") == 0 || strcmp(args[ i ], "-key") == 0)
			{
				iKey = i;
			}
			if ( strcmp(args[ i ],"--s") == 0 || strcmp(args[ i ],"--string") == 0)
			{
				iString = i;
			}
		}


		if( iKey = 0 || iString == 0 )
		{
			printf( "No se encontraron los parámetros correspondientes\n" );
			printf( "[ --k , -key ] - [ --s , -string ] \n" );
		}
		else
		{
            char CopiedString[ 15 ], TheKeyMen[ 10 ];
            memset( CopiedString, '\0', sizeof(CopiedString) );
            memset( TheKeyMen, '\0', sizeof(TheKeyMen));
            strcpy( args[ iKey + 2 ] , TheKeyMen );
            strcpy( args[ iString + 1 ], CopiedString);


            int ilen = strlen( CopiedString );
			printf( "==========================\n" );
			printf( "Key = %s\n" , TheKeyMen );
			printf( "Texto ingresado = -%s- \n", CopiedString );
			CryptString( CopiedString , ilen, TheKeyMen );
			printf( "Texto saliente =  -%s- \n" , CopiedString);
			printf( "==========================\n" );
		}


	}
	else
	{
		printf( "4 (Cuatro) parámetros requeridos! \n" );
		printf( "[ --k , -key ] - [ --s , -string ] \n" );
	}


}



```

---

