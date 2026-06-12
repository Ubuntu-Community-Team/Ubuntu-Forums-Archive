---
title: "Problem with a Programming Asignment"
date: 2011-09-19
forum: Programming Talk
---

### Post by antoplant on 2011-09-19
Hi I was hoping someone could help me with this assignment I have for a UNIX Operating Systems class. I am supposed to write a C program, fdump to examine a text file and create a new dump file showing the 
contents of a text file as ASCII, hex and binary, ignoring new line characters.   Your program 
should accept your input and output file names as command line arguments. I need to know how to convert everything in the input file to hex and binary. 
This is what I have so far:


{
       int main(int argc, char *argv[])
        int fd, output;
        if(argc != 3)
        {
                fprintf(stderr, "ERROR\n");
                return 1;
        }
        if(( fd = open(argv[1], O_RDONLY | O_CREAT, S_IRUSR))== -1)
        {
                fprintf(stderr, "Could not open %s \n", argv[1]);
                return 1;
        }
        if(( output = open(argv[2], O_WRONLY | O_CREAT, S_IWUSR)) == -1)
        {
                fprintf(stderr, "Could not open %s \n", argv[2]);
                return 1;
        }

        return 0;
}
{
        input=1;
        out=write(out,"Loc ", 4)
        out=write(out,"Char ",6)
        out=write(out,"Hex ",4)
        out=write(out,"Binary ",7)
}

---

### Post by sisco311 on 2011-09-19
Homework.

Thread closed.

---

