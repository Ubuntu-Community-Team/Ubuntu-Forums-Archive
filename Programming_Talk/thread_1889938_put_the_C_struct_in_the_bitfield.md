---
title: "put the C struct in the bitfield"
date: 2011-12-02
forum: Programming Talk
---

### Post by cybo on 2011-12-02
i have an interesting problem. 

i need to create a structure in C that will share bits with a regular uint16 and have a union. something like the following:

```
typedef struct {
  uint16 field0:4,
         struct {
           uinion {
             uint16 field1:3,
                    field2:4,
                    field3:5;

             uint16 field4:4,
                    field5:3,
                    field6:5;

             uint16 field7:5,
                    field8:4,
                    field9:3;
           } u
         } MyOtherStruct
} MyStruct;

```

the idea is to store MyStruct as a two byte variable of uint16. First four bits are occupied by field0. i use fields i need (field1..field9) based on the value of field0.

say field0 is 1, then i will use field1..field3
if field0 is 2, then i will use field4..filed6
if field0 is 3 then i will use field7..field9

does anybody have any ideas on how to implement this struct, or even if it is possible in C? or maybe someone has another solution to my problem. 

any help is appreciated.

p.s. if anyone is wondering this is not a homework question. i'm happily employed and this is one of the problems we encountered at my work.

---

### Post by Bachstelze on 2011-12-02
I have tried some things using stuct with bitfields and unions, but the compiler always complains about the structs having incomplete type, so I can't use them as members of an union... One less elegant way would be to use bitwise logical and shifting operations to place the bits at the correct place.

---

### Post by ofnuts on 2011-12-02
Something like this:
```

typedef unsigned short int uint16;

union uint16map {
    uint16 intValue;
    uint16 type:4;
    struct {
        uint16 type:4,
               field1:3,
               field2:4,
               field3:5;
    } map1;
    struct {
        uint16 type:4,
               field1:4,
               field2:4,
               field3:4;
    } map2;
};

int main(int argc, char **argv) {
    union uint16map map;
    map.intValue=0b1101101110011111;
    
    printf("Type: %d: Map1: %d,%d,%d\n",map.type,map.map1.field1,map.map1.field2,map.map1.field3);
    printf("Type: %d: Map2: %d,%d,%d\n",map.type,map.map2.field1,map.map2.field2,map.map2.field3);
    return 0;
}

[I][B]Type: 15: Map1: 1,7,27
Type: 15: Map2: 9,11,13[/B][/I]

```Of course the 4 bits if the "type" field have to appear in all your uint16 bitfields to shift the relevant ones to their proper position. I declared them with the same name to make their purpose more obvious but you can also use the anonymous declaration if you don't use them, i.e.:
```

    struct {
        uint16 :4,
               field1:3,
               field2:4,
               field3:5;
    } map1;

```

---

### Post by cybo on 2011-12-05
thanks. that actually might work for me.

---

