---
title: "C++ memset crashes program... why ?"
date: 2009-11-07
forum: Programming Talk
---

### Post by WitchCraft on 2009-11-07
I have made a program which calculates the standard deviation.

My problem is, when I used memset to initialize the array FragArray, then my program crashes.

The problem is the memset.
If I omit the memset, then it doesn't crash.

What's wrong with the memset?

Here my code:
```



/*
average
squaredist=(frags[i]- average)^2
sum(squaredist[i])
sumdivn = sum/(n)
sample_sumdivn = sum/(n-1)
sample_sigma = sqrt(sample_sumdivn)
sigma = sqrt(sumdivn)

*/

#include <iostream>
#include <cstdlib>
#include <cmath>


template <class DataType>
DataType generic_abs(DataType dt_Data)
{
	if (dt_Data < (static_cast<DataType>  (0.0)))
		dt_Data = dt_Data * (static_cast<DataType> (-1.0)) ;
	return static_cast<DataType> (dt_Data) ;
}


inline int FuncRandomNumberInRange( int intMinInRange,	int intMaxInRange )
{
    return ( rand() % (intMaxInRange - intMinInRange + 1) ) + intMinInRange ;
}



typedef struct 
{
	int kills;
	int killed ;
	double kills_killed_ratio;
	bool isValid ;
} FragArray_t;


FragArray_t FragArray[100] ;

int main()
{
	memset( (void*) FragArray, 0, sizeof(FragArray)*100);
	//memset( (void*) &FragArray, 0, sizeof(FragArray)*100);
	//memset( (void*) FragArray[0], 0, sizeof(FragArray)*100);
	//memset( (void*) &FragArray[0], 0, sizeof(FragArray)*100);

	for(int i = 0; i< 100; ++i)
	{
		FragArray[i].kills = FuncRandomNumberInRange(0, 10);
		FragArray[i].killed = FuncRandomNumberInRange(0, 10);
		FragArray[i].kills_killed_ratio = (double) (FragArray[i].kills+1) / (double) (FragArray[i].killed + 1) ;
		FragArray[i].isValid = (bool) FuncRandomNumberInRange(0,1);
	}

	double average_kills = 0;
	double average_killed = 0;
	double average_ratio = 0;
	
	int n = 0;
	for(int i = 0; i< 10; ++i)
	{
		if(FragArray[i].isValid)
		{
			++n;
			average_kills += (double) FragArray[i].kills;
			average_killed += (double) FragArray[i].killed;
			average_ratio += FragArray[i].kills_killed_ratio;
		}
		printf("FragArray[%d].kills = %d, killed = %d, ratio = %d, isValid = %d\n", i, FragArray[i].kills, FragArray[i].killed, FragArray[i].kills_killed_ratio, FragArray[i].isValid);
	}
	
	average_kills = average_kills / (double ) n;
	average_killed = average_killed / (double ) n;
	average_ratio = average_ratio / (double ) n;

	printf("Average kills: %f, average killed: %f, average ratio: %f.\n",average_kills,average_killed,average_ratio);


	double sum_kills = 0;
	double sum_killed = 0;
	double sum_ratio = 0;
	for(int i = 0; i< 10; ++i)
	{
		if(FragArray[i].isValid)
		{
			++n;
			sum_kills += std::pow(( (double) FragArray[i].kills - average_kills),2);
			sum_killed +=std::pow(( (double) FragArray[i].killed - average_killed),2);
			sum_ratio += std::pow((FragArray[i].kills_killed_ratio - average_ratio),2);
		}
	}

	sum_kills = sum_kills / (double) n;
	sum_killed = sum_killed / (double) n;
	sum_ratio = sum_ratio / (double) n;
	printf("sum Average kills: %f, sum average killed: %f, sum average ratio: %f.\n",sum_kills,sum_killed,sum_ratio);
	
	double sigma_kills = std::sqrt(sum_kills);
	double sigma_killed= std::sqrt(sum_killed);
	double sigma_ratio = std::sqrt(sum_ratio);
	printf("sigma kills: %f, sigma killed: %f, sigma ratio: %f.\n",sigma_kills,sigma_killed,sigma_ratio);
	


	return EXIT_SUCCESS ;
}


```

---

### Post by WitchCraft on 2009-11-07
Oh, is it:
```

memset( (void*) FragArray, 0, sizeof(FragArray[0])*100);

```

?

---

### Post by WitchCraft on 2009-11-07
Oh, no, should have been:
```

memset( (void*) &FragArray, 0, sizeof(FragArray_t)*100);

```
:lolflag:


Edit:
Even better:
```

memset( (void*) &FragArray, 0, sizeof(FragArray_t) * sizeof(FragArray) / sizeof(FragArray[0]));

```
Looks far more cryptic, but is the same as
```

memset( (void*) &FragArray, 0, sizeof(FragArray) );

```

---

### Post by WitchCraft on 2009-11-07
It works.
DoStatistics finds players whose score's exceeds all player's average by 3 times standard deviation.
Anybody has a comment on this kind of cheat detection (bug/error/suggestion)?

```



/*
average
squaredist=(frags[i]- average)^^2
sum(squaredist[i])
sumdivn = sum/(n)
sample_sumdivn = sum/(n-1)
sample_sigma = sqrt(sample_sumdivn)
sigma = sqrt(sumdivn)

*/

#include <iostream>
#include <cstdlib>
#include <cmath>
#include <cstdarg>


template <class DataType>
DataType generic_abs(DataType dt_Data)
{
	if (dt_Data < (static_cast<DataType>  (0.0)))
		dt_Data = dt_Data * (static_cast<DataType> (-1.0)) ;
	return static_cast<DataType> (dt_Data) ;
}



template <class DataType>
bool generic_sign(DataType dt_Data)
{
	if (dt_Data < (static_cast<DataType>  (0.0)))
		return false;
	return true;
}






inline int FuncRandomNumberInRange( int intMinInRange,	int intMaxInRange )
{
    return ( rand() % (intMaxInRange - intMinInRange + 1) ) + intMinInRange ;
}



typedef struct 
{
	int kills;
	int killed ;
	double kills_killed_ratio;
	bool isValid ;
} PlayerStatistics_t;


PlayerStatistics_t PlayerStatistics[100] ;

void doStatistics();

int main()
{
	memset( (void*) &PlayerStatistics, 0, sizeof(PlayerStatistics_t) * sizeof(PlayerStatistics) / sizeof(PlayerStatistics[0]));
	
	
	for(int i = 0; i< 10; ++i)
	{
		PlayerStatistics[i].kills = FuncRandomNumberInRange(0, 10);
		PlayerStatistics[i].killed = FuncRandomNumberInRange(0, 10);
		PlayerStatistics[i].kills_killed_ratio = (double) (PlayerStatistics[i].kills+1) / (double) (PlayerStatistics[i].killed + 1) ;
		//PlayerStatistics[i].isValid = (bool) FuncRandomNumberInRange(0,1);
		PlayerStatistics[i].isValid = true;
	}
	
	
	PlayerStatistics[5].kills=20;
	PlayerStatistics[5].killed= 0;
	PlayerStatistics[5].kills_killed_ratio = (double) (PlayerStatistics[5].kills+1) / (double) (PlayerStatistics[5].killed + 1) ;
	PlayerStatistics[5].isValid= true;


	doStatistics();


	return EXIT_SUCCESS ;
}






/*
void QDECL CG_Printf(const char *msg, ...)
{
	va_list argptr  ;
	char text[1024] ;

	va_start(argptr, msg) ;
		vsprintf(text, msg, argptr) ;
	va_end(argptr)        ;

	trap_CG_Print(text)   ;
}


//void QDECL Com_Printf(const char *msg, ...) // fixed
void __attribute__ ((format (printf, 1, 2)))  QDECL Com_Printf( const char *msg, ... )
{
	va_list argptr  ;
	char text[1024] ;

	va_start(argptr, msg) ;
		vsprintf(text, msg, argptr) ;
	va_end(argptr) ;

	CG_Printf("%s", text) ;
}
*/


void Con_Printf (char* format, ...)
{
  va_list args;
  va_start (args, format);
	vprintf (format, args);
  va_end (args);
}


void InvalidatePlayer(int iSlotNumber)
{
	PlayerStatistics[iSlotNumber].isValid = false;
	PlayerStatistics[iSlotNumber].kills = 0;
	PlayerStatistics[iSlotNumber].killed = 0;
	PlayerStatistics[iSlotNumber].kills_killed_ratio = 0.0;
}




void doStatistics()
{
	double average_kills = 0;
	double average_killed = 0;
	double average_ratio = 0;
	
	int n = 0;
	for(int i = 0; i< 10; ++i)
	{
		if(PlayerStatistics[i].isValid)
		{
			++n;
			average_kills += (double) PlayerStatistics[i].kills;
			average_killed += (double) PlayerStatistics[i].killed;
			average_ratio += PlayerStatistics[i].kills_killed_ratio;
		}
		Con_Printf("PlayerStatistics[%d].kills = %d, killed = %d, ratio = %f, isValid = %d\n", i, PlayerStatistics[i].kills, PlayerStatistics[i].killed, PlayerStatistics[i].kills_killed_ratio, PlayerStatistics[i].isValid);
	}
	

	
	
	if(n==0) // No, you're not gonna get me, not this time
		n=1;
	
	average_kills = average_kills / (double ) n;
	average_killed = average_killed / (double ) n;
	average_ratio = average_ratio / (double ) n;

	Con_Printf("Average kills: %f, average killed: %f, average ratio: %f.\n",average_kills,average_killed,average_ratio);


	double sum_kills = 0;
	double sum_killed = 0;
	double sum_ratio = 0;
	for(int i = 0; i< 10; ++i)
	{
		if(PlayerStatistics[i].isValid)
		{
			++n;
			sum_kills += std::pow(( (double) PlayerStatistics[i].kills - average_kills),2);
			sum_killed +=std::pow(( (double) PlayerStatistics[i].killed - average_killed),2);
			sum_ratio += std::pow((PlayerStatistics[i].kills_killed_ratio - average_ratio),2);
		}
	}

	Con_Printf("sum Average kills: %f, sum average killed: %f, sum average ratio: %f.\n",sum_kills,sum_killed,sum_ratio);

	sum_kills = sum_kills / (double) n;
	sum_killed = sum_killed / (double) n;
	sum_ratio = sum_ratio / (double) n;
	
	Con_Printf("Average kills: %f, average killed: %f, average ratio: %f.\n",sum_kills,sum_killed,sum_ratio);
	
	double sigma_kills = std::sqrt(sum_kills);
	double sigma_killed= std::sqrt(sum_killed);
	double sigma_ratio = std::sqrt(sum_ratio);
	Con_Printf("sigma kills: %f, sigma killed: %f, sigma ratio: %f.\n",sigma_kills,sigma_killed,sigma_ratio);
	

	for(int i = 0; i< 100; ++i)
	{
		if (PlayerStatistics[i].isValid)
		{
			double killdiff = (double) PlayerStatistics[i].kills - average_kills;
			//double killeddiff = (double) PlayerStatistics[i].killed - average_killed;
			double ratiodiff = (double) PlayerStatistics[i].kills_killed_ratio - average_ratio;
			
			//double abskilldiff = generic_abs(killdiff);
			//double abskilleddiff = generic_abs(killeddiff);
			//double absratiodiff = generic_abs(ratiodiff);
			
			//if(killdiff<0.0)
			if(PlayerStatistics[i].kills_killed_ratio < 1.0)
			{
				Con_Printf("Player[%d] sucks...\n", i);
				continue ;
			}
			
			/*
			if(killdiff>0.0)
			{
				double times = killdiff/sigma_kills ;
				Con_Printf("Player[%d]'s kills is within reach of %f times standard deviation...\n", i, times);
				
				if(times > 3.0)
				{
					Con_Printf("Player[%d]'s kill score exceeds 3 times standard deviation. Definitely a CHEATER ! \n", i);
				}
			}
			*/
			
			
			if(ratiodiff > sigma_ratio)
			{
				double times = ratiodiff /sigma_ratio ;
				Con_Printf("Player[%d]'s kills killed ratio is within reach of %f times standard deviation...\n", i, times);
				
				if(times > 3.0)
				{
					Con_Printf("Player[%d]'s kill killed ratio exceeds 3 times standard deviation. Definitely a CHEATER ! \n", i);
				}
			}
			
			
			
			
			
			
			
			
			
			
			
			
			
			
			//killeddiff < 0.0 || ratiodiff)
			//Con_Printf("diff kills: %f, diff killed: %f, diff ratio: %f.\n",killdiff,killeddiff,ratiodiff);
		}
		
	}
	
}


```

---

### Post by efexD on 2009-11-07
the real question is, why the **hell** are you using memset in _C++_

---

### Post by MadCow108 on 2009-11-07
probably for the same reason the code has not a single C++ construct in it.
(except from the [not-really-]generic_abs and [not-really-]generic_sign function [they depend on an implicit conversion to float])

You should familiarize yourself with the STL. Its containers, Function objects and algorithms will clean up your code considerably.
Also you should give your PlayerStatistics_t struct a default constructor initializing it, then you don't need the memset anymore.

---

### Post by WitchCraft on 2009-11-08
> **MadCow108 said:**
> probably for the same reason the code has not a single C++ construct in it.
(except from the [not-really-]generic_abs and [not-really-]generic_sign function [they depend on an implicit conversion to float])

You should familiarize yourself with the STL. Its containers, Function objects and algorithms will clean up your code considerably.
Also you should give your PlayerStatistics_t struct a default constructor initializing it, then you don't need the memset anymore.

I use it in Quake3, which was originally written in C, so I have to keep it simple.

---

### Post by jnah on 2009-11-20
As a quick example explanation, and a bit late.....

int32 array[100];

sizeof(array[0]) == 4   // an int32 is 4 bytes

sizeof(array) == 400   // the toal size of bytes allocated to the array by compiler

sizeof(array)/sizeof(array[0]) = 100   // number of items in array.

---

### Post by WitchCraft on 2009-11-26
> **jnah said:**
> As a quick example explanation, and a bit late.....

int32 array[100];

sizeof(array[0]) == 4   // an int32 is 4 bytes

sizeof(array) == 400   // the toal size of bytes allocated to the array by compiler

sizeof(array)/sizeof(array[0]) = 100   // number of items in array.

Yep, I realized that.
It's very useful when you have an array you grow dynamically and loop over it.

You just loop over n= sizeof(array)/sizeof(array[0]) times

---

### Post by MadCow108 on 2009-11-26
> **WitchCraft said:**
> Yep, I realized that.
It's very useful when you have an array you grow dynamically and loop over it.

You just loop over n= sizeof(array)/sizeof(array[0]) times


woa big mistake!
sizeof does _NOT_ work on dynamic arrays
it only works on stuff known at compile time.
and even then the implicit conversion from array to pointer breaks sizeof too.
e.g. when passing an array to a function taking a pointer to memory block

---

### Post by WitchCraft on 2009-11-26
> **MadCow108 said:**
> woa big mistake!
and even then the implicit conversion from array to pointer breaks sizeof too.
e.g. when passing an array to a function taking a pointer to memory block

Argh, that it doesn't work on dynamic arrays, and on char* strings, that I knew, but I didn't know that it doesn't work when you convert the array to a pointer in general.

Well, now I know. Thanks for the correction.

---

