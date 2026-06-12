---
title: "CL calculator"
date: 2008-01-10
forum: Programming Talk
---

### Post by mike_g on 2008-01-10
When I did C in college I always wondered if there was any point to the command line progs we used to have to make; now I'm using Linux it seems they may have a use after all :)

Anyway,  heres a simple calculator prog I knocked up that could come in handy from time to time:
```
#include <stdio.h>
#include <stdlib.h>

double Calc(double left, char op, double right)
{
	switch(op)
	{
		case '+': return left + right;
		case '-': return left - right;
		case 'x': return left * right;
		case '/': return left / right;
		default:
			printf("Invalid operator.\nValid ops: + - x /\n");
			exit(EXIT_FAILURE);
	}
}

int main(int argc, char* argv[])
{
	if(argc < 4)
	{
		printf("Error: Not enough parameters.\n");
		exit(EXIT_FAILURE);
	}
	if(argc % 2)
	{
		printf("Error: Invalid parameters.\n");
		exit(EXIT_FAILURE);
	}
	double left=strtod(argv[1], NULL), right;	
	int i;	
	for(i=2; i<argc; i+=2)
	{
		right = strtod(argv[i+1], NULL);
		left = Calc(left, argv[i][0], right);
	}
	printf("%f\n", left);
	exit(EXIT_SUCCESS);
}
```

It read expressions from left to right, as opposed to BODMAS ordering. Also each operator/operand needs to be split by a space. It would probably be better if the entire expression was fed into the prog as a single srting then broke down, but that would require a whole load of extra code which would spoil the simplicity of it all. 

Anyway, have fun :)

---

