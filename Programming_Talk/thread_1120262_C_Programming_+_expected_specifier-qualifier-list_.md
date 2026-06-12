---
title: "C Programming + expected specifier-qualifier-list before [varname]"
date: 2009-04-08
forum: Programming Talk
---

### Post by nova47 on 2009-04-08
I'm writing a simulation of a 4 stage pipelined processor for a class at school and this error is driving me up a wall. I'm more specifically interested in what the heck  "expected specifier-qualifier-list before [varname]" means rather than just a fix for the code below. Anyway here's the code (I've marked where I get the error):

[PHP]

/*
 * cpu.h -- This file is for the model of the SCMP CPU.
 * Author: Grant Curell
 */

#ifndef CPU_H
#define CPU_H

#include <time.h>
#include "memory.h"

#define NUM_REGS	32	// 32 registers
#define true 1 //define the boolean value "true" to be 1
#define false 0 //define the boolean value "false to be 0

// struct for CPU
typedef struct {
   int regs[NUM_REGS];	// CPU registers
   unsigned long long clock;	// 64-bit clock
   unsigned long long latched_clock;	// latched version of clock
   Memory memory;	// system memory
   int ip;		// instruction pointer
   int ir;		// instruction register
   IFID ifid; //ONE ERROR IS RIGHT HERE
   IDEX idex;
   IDIF idif;
   EXWB exwb;
} CPU;

// struct for IFID register
// contains IP, IR, branchFlag, branchIP, stallFlag
typedef struct {
	int ip;	//instruction pointer
	int ir;	//instruction register
} IFID;

// struct for IDEX register
// contains opcode, rd, operands, IP
typedef struct {
	Instr *instr; //THE OTHER IS HERE
	int opcode;
	int rd;
	int ip;
} IDEX;

// struct for IDIF register
// contains opcode, rd, operands, IP
typedef struct {
	int stallflag;
	int branchIP;
	int branchFlag;
} IDIF;

// struct for exid register
// contains the result of the alu operation
typedef struct {
	int rd;
} EXID;

// struct for exwb register
// contains ip
typedef struct {
	int ip;
	int writeFlag;
	int opcode;
	int rd;
	int result;
} EXWB;

// function prototypes
int getReg( CPU *cpu, int reg );
void setReg( CPU *cpu, int reg, int val );
int getClkl( CPU *cpu );
int getClkh( CPU *cpu );
void init( CPU *cpu, int argc, char *argv[] );
void finish( CPU *cpu, clock_t elapsedTime );
int simulateCycle( CPU *cpu );

#endif

[/PHP]

---

### Post by Firestom on 2009-04-08
The problem is the order in which your structures are declared. You should declare your sub-structures over the main one. Else, the compiler reads your code from top to bottom and doesn't know what  IFID, IDEX, IDIF, EXWB stands for.

Or you put the prototypes for your structures over the main one or you just place your sub-structures over the main one (CPU).

> **nova47 said:**
> I'm writing a simulation of a 4 stage pipelined processor for a class at school and this error is driving me up a wall. I'm more specifically interested in what the heck  "expected specifier-qualifier-list before [varname]" means rather than just a fix for the code below. Anyway here's the code (I've marked where I get the error):

[PHP]

/*
 * cpu.h -- This file is for the model of the SCMP CPU.
 * Author: Grant Curell
 */

#ifndef CPU_H
#define CPU_H

#include <time.h>
#include "memory.h"

#define NUM_REGS	32	// 32 registers
#define true 1 //define the boolean value "true" to be 1
#define false 0 //define the boolean value "false to be 0

//Prototypes (Typedef) for structures
typedef struct IFID IFID;
typedef struct IDEX IDEX;
typedef struct IDIF IDIF;
typedef struct EXID EXID;
typedef struct EXWB EXWB;

// struct for CPU
typedef struct {
   int regs[NUM_REGS];	// CPU registers
   unsigned long long clock;	// 64-bit clock
   unsigned long long latched_clock;	// latched version of clock
   Memory memory;	// system memory
   int ip;		// instruction pointer
   int ir;		// instruction register
   IFID ifid; //ONE ERROR IS RIGHT HERE
   IDEX idex;
   IDIF idif;
   EXWB exwb;
} CPU;

// struct for IFID register
// contains IP, IR, branchFlag, branchIP, stallFlag
struct IFID{
	int ip;	//instruction pointer
	int ir;	//instruction register
};

// struct for IDEX register
// contains opcode, rd, operands, IP
struct IDEX{
	Instr *instr; //THE OTHER IS HERE
	int opcode;
	int rd;
	int ip;
};

// struct for IDIF register
// contains opcode, rd, operands, IP
struct IDIF{
	int stallflag;
	int branchIP;
	int branchFlag;
};

// struct for exid register
// contains the result of the alu operation
struct EXID{
	int rd;
};

// struct for exwb register
// contains ip
struct EXWB{
	int ip;
	int writeFlag;
	int opcode;
	int rd;
	int result;
};

// function prototypes
int getReg( CPU *cpu, int reg );
void setReg( CPU *cpu, int reg, int val );
int getClkl( CPU *cpu );
int getClkh( CPU *cpu );
void init( CPU *cpu, int argc, char *argv[] );
void finish( CPU *cpu, clock_t elapsedTime );
int simulateCycle( CPU *cpu );

#endif

[/PHP]

---

### Post by nova47 on 2009-04-08
Thank you so much got it up and running. I hate those errors that you stare at for half an hour and get nowhere and the answer was just that obvious :-p

---

### Post by Firestom on 2009-04-08
That's what the forum is for, dear user! If ever you're stumped, you can ask anybody here to help you out, there's no problem. People like me love when they can lend a hand to someone needing help, it makes us feel like we're doing it good and make us feel intelligent!

Keep us the good work, I didn't quite understand what is does but good work. And for information, a type-specifier is the term used for the keywords that tell which type it is (int, double, char*, struct). If you make a little research on terms you don't understand you might come up with a solution fast!

---

### Post by soltanis on 2009-04-08
Solved already but yeah for future note, C reads files top to bottom, so either your structs need to be in the right order or use the prototypes as above.

BTW I didn't catch in your code where you defined the type Instr. Where is that at?

---

### Post by nova47 on 2009-04-09
It's not defined in the code above. That's only a small snippet of the entire program. Instr is defined in another filed aptly named instr.h. Actually the problem I'm having at the moment is that in the code I posted above I need to include instr.h (for the Instr definition) and in instr.h I need cpu.h (the code that I posted) because it needs the CPU struct definition so I haven't decided how I'm going to fix that.

---

### Post by Habbit on 2009-04-09
If you don't need the whole CPU structu embedded in each Instr struct, you can define Instr like this: ```

typedef struct CPU CPU;

typedef struct Instr {
   /* whatever */
   CPU* cpu;
   /* more members */
} Instr;
```You can declare _pointers_ to incomplete types because all the compiler has to know is the size and alignment of the data type it's going to put into the struct (which is sizeof(CPU*) == sizeof(void*)). You'd only need to have the complete definition when you try to do something like "my_instr.cpu->ip". This is a very usual way to deal with circular dependences.

---

### Post by nova47 on 2009-04-09
What I ended up having to do was a forward declaration:

[PHP]
/*
 * cpu -- This file is for the model of the SCMP CPU.
 * Author: Grant Curell
 */

#ifndef CPU_H
#define CPU_H

#include <time.h>
#include "memory.h"

struct InstrStruct;

#define NUM_REGS	32	// 32 registers
#define true 1 //define the boolean value "true" to be 1
#define false 0 //define the boolean value "false to be 0

// struct for IFID register
// contains IP, IR, branchFlag, branchIP, stallFlag
typedef struct {
	struct InstrStruct *instr;
	int ir;
	int ip;
} IFID;

// struct for IDEX register
// contains opcode, rd, operands, IP
typedef struct {
	struct InstrStruct *instr;
	int ip;
} IDEX;

// struct for IDIF register
// contains opcode, rd, operands, IP
typedef struct {
	int stallFlag;
	int branchIP;
	int branchFlag;
} IDIF;

// struct for exid register
// contains the result of the alu operation
typedef struct {
	int rd;
} EXID;

// struct for exwb register
// contains ip
typedef struct {
	struct InstrStruct *instr;
	int result;
} EXWB;

// struct for CPU
typedef struct {
   int regs[NUM_REGS];	// CPU registers
   unsigned long long clock;	// 64-bit clock
   unsigned long long latched_clock;	// latched version of clock
   Memory memory;	// system memory
   int ip;		// instruction pointer
   int ir;		// instruction register
   IFID ifid;
   IDEX idex;
   IDIF idif;
   EXWB exwb;
   EXID exid;
} CPU;

// function prototypes
int getReg( CPU *cpu, int reg );
void setReg( CPU *cpu, int reg, int val );
int getClkl( CPU *cpu );
int getClkh( CPU *cpu );
void init( CPU *cpu, int argc, char *argv[] );
void finish( CPU *cpu, clock_t elapsedTime );
int simulateCycle( CPU *cpu );

#endif
[/PHP]

That got around having to include instr.h in cpu.h I just had to replace Instr *instr; with struct InstrStruct *instr;

---

