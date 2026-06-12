---
title: "C hash of array, hash of hash, etc."
date: 2013-10-24
forum: Programming Talk
---

### Post by hailholyghost on 2013-10-24
Hello,

in perl I frequently store data in hashes of arrays, e.g. $data{beta2}[1701].  This allows me to do a lot with the data in very few lines of code.

However, I am very curious about how to do this in C.  For example, if I have

```

my %data;
my @torsions = qw(alpha2 alpha3 alpha4 beta2 beta3 beta4 gamma1 gamma2 gamma3 gamma4 epsilon1 epsilon2 epsilon3 zeta1 zeta2 zeta3 chi1 chi2 chi3 chi4);
foreach my $tor (@torsions) {
   open(FH,"<$tor") or die "cannot read $tor: $!";
   while (<FH>) {
      if (/\d+\.\d+\s+(\d+)\.(\d+)/) {
         push(@{ data{$tor}, "$1.$2");
      }
   }
   close FH;
}

```

The current version I have of this in C is about 200 lines long, tedious to write and work with the data, and is very difficult to read.  How could I write this code in C?

Thanks so much!

---

### Post by Vaphell on 2013-10-24
maybe you describe what it does in plain english, not many people can read perl incantations.

---

### Post by hailholyghost on 2013-10-24
Hi Vaphell,

The idea is to store all of the data from these files in one large hash, e.g. instead of manually creating bulky multidimensional arrays and reading data to each of 20 arrays separately:
```

       double (*alpha)[3], (*beta)[3], (*gamma)[4], (*chi)[4], (*epsilon)[3], (*zeta)[3];
       alpha = malloc(length*sizeof(double)*3);
       beta = malloc(length*sizeof(double)*3);
       gamma = malloc(length*sizeof(double)*4);
       epsilon = malloc(length*sizeof(double)*3);
       chi = malloc(length*sizeof(double)*4);
       zeta = malloc(length*sizeof(double)*3);
       for (unsigned int nuc = 2; nuc <= 4; nuc++) {//read in torsions with 3 present
//read in alpha
          sprintf(file,"%salpha%u",simulation,nuc);
          FILE *fh;
          fh = fopen(file,"r");
          if (fh != NULL) {
             unsigned int c = 0;
             while(!feof(fh)) {
                if (fscanf(fh,"%f %lf",&time,&alpha[nuc-2][c]) != 2) {
                   continue;
                }
                if (alpha[nuc-2][c] < 0.0) {
                   alpha[nuc-2][c] += 360.0;
                }
             }
          } else {
             printf("Could not read %s.\n",file);
             exit(EXIT_FAILURE);
          }
//read in beta
          sprintf(file,"%sbeta%u",simulation,nuc);
          fh = fopen(file,"r");
          if (fh != NULL) {
             unsigned int c = 0;
             while(!feof(fh)) {
                if (fscanf(fh,"%f %lf",&time,&beta[nuc-2][c]) != 2) {
                   continue;
                }
                if (beta[nuc-2][c] < 0.0) {
                   beta[nuc-2][c] += 360.0;
                }
             }
          } else {
             printf("Could not read %s.\n",file);
             exit(EXIT_FAILURE);
          }
//read in zeta
          sprintf(file,"%szeta%u",simulation,nuc-1);
          fh = fopen(file,"r");
          if (fh != NULL) {
             unsigned int c = 0;
             while(!feof(fh)) {
                if (fscanf(fh,"%f %lf",&time,&zeta[nuc-1][c]) != 2) {
                   continue;
                }
                if (zeta[nuc-1][c] < 0.0) {
                   zeta[nuc-1][c] += 360.0;
                }
             }
          } else {
             printf("Could not read %s.\n",file);
             exit(EXIT_FAILURE);
          }
//read in epsilon
          sprintf(file,"%sepsilon%u",simulation,nuc-1);
          fh = fopen(file,"r");
          if (fh != NULL) {
             unsigned int c = 0;
             while(!feof(fh)) {
                if (fscanf(fh,"%f %lf",&time,&epsilon[nuc-1][c]) != 2) {
                   continue;
                }
                if (epsilon[nuc-1][c] < 0.0) {
                   epsilon[nuc-1][c] += 360.0;
                }
             }
          } else {
             printf("Could not read %s.\n",file);
             exit(EXIT_FAILURE);
          }
       }
       for (unsigned int nuc = 1; nuc <= 4; nuc++) {
//read in gamma
          sprintf(file,"%sgamma%u",simulation,nuc);
          FILE *fh;
          fh = fopen(file,"r");
          if (fh != NULL) {
             unsigned int c = 0;
             while(!feof(fh)) {
                if (fscanf(fh,"%f %lf",&time,&gamma[nuc-1][c]) != 2) {
                   continue;
                }
                if (gamma[nuc-1][c] < 0.0) {
                   gamma[nuc-1][c] += 360.0;
                }
             }
          } else {
             printf("Could not read %s.\n",file);
             exit(EXIT_FAILURE);
          }
//read in chi
          sprintf(file,"%schi%u",simulation,nuc);
          fh = fopen(file,"r");
          if (fh != NULL) {
             unsigned int c = 0;
             while(!feof(fh)) {
                if (fscanf(fh,"%f %lf",&time,&chi[nuc-1][c]) != 2) {
                   continue;
                }
                if (chi[nuc-1][c] < 0.0) {
                   chi[nuc-1][c] += 360.0;
                }
             }
          } else {
             printf("Could not read %s.\n",file);
             exit(EXIT_FAILURE);
          }
       }
//free memory for each torsion stored in memory
       free(alpha); alpha = NULL;
       free(beta); beta = NULL;
       free(gamma); gamma = NULL;
       free(epsilon); epsilon = NULL;
       free(zeta); zeta = NULL;
       free(chi); chi = NULL;

```

This code works just fine (this is a snippet from the complete program code).  This is pretty cumbersome and lengthy, and I want other people to be able to easily read it in as few lines as possible in C, which more people know than perl, is faster, and is almost universally installed.  Also, as you said, perl is often criticized for being difficult to read.

In perl I can run this equivalent in 11 lines.  How I could write this in a C hash/associative array/whatever in something like Perl's

```

push($data{$file},$variable)

```

which can be accessed from 

```

$data{$file}[$index]

```

in C?

Thanks for your time :)

---

### Post by Vaphell on 2013-10-24
does it have to be C? In C++ you have STL with maps, vectors and whatnot.

---

### Post by Bachstelze on 2013-10-24
Remark: pasting code from an existing program is almost never appropriate as an example.

---

### Post by ofnuts on 2013-10-24
> **hailholyghost said:**
> Hi Vaphell,

The idea is to store all of the data from these files in one large hash, e.g. instead of manually creating bulky multidimensional arrays and reading data to each of 20 arrays separately:

This code works just fine (this is a snippet from the complete program code).  This is pretty cumbersome and lengthy, and I want other people to be able to easily read it in as few lines as possible in C, which more people know than perl, is faster, and is almost universally installed.  Also, as you said, perl is often criticized for being difficult to read.

In perl I can run this equivalent in 11 lines.  How I could write this in a C hash/associative array/whatever in something like Perl's

```

push($data{$file},$variable)

```

which can be accessed from 

```

$data{$file}[$index]

```

in C?

Thanks for your time :)

Some thoughts:

[LIST=1]
[*]If C code that can run 10x faster than Perl code could be as terse, there would be no need for Perl
[*]I see an awful lot of duplication in the C code... The 6 pieces of code that read files could be one single function called 6 times.
[*]Is this code working? I don't see the "c" variables incremented (nor their values tested against "length")
[/LIST]

---

### Post by drmrgd on 2013-10-24
> **Vaphell said:**
> maybe you describe what it does in plain english, not many people can read perl incantations.

LOL @ incantations!

The script the OP posted, starts with an array of filenames stored in '@torsions'.  Then the user is opening each file in that array one at a time (referring to each one as "$tor") and reading it line by line.  If the line in the file matches the regex (note the captures):

```

/\d+\.\d+\s+(\d+)\.(\d+)/

```

Then the data is being stored in a hash of arrays with a structure like so (curly brace items indicate a hash (dict in python), and square brackets indicate an array ):

```

{
    'alpha2'  =>
        [
             "$1,$2"
        ],
      'alpha3'  =>
        [
            "$1,$2"
        ],
    .
    .
    .
}

```

Note that there's a typo in the push, that should read:

```

push( @{$data{$tor}}, "$1,$2" );

```

And, given that the user has asked to create a hash of arrays, I think that actually the '"$1,$2"' is not quite correct and those variables should not be quoted.  As it stand, I think that just creates a one element array, unless there is overlap with a key name, which I don't see in the given array above.

From a brief excursion with C (which I intend to get back to once the dust settles on a few other things I'm working on at the moment), I can say that this is not so easy in C and is probably one of the reasons people took to and really liked Perl when it came out.

---

### Post by Vaphell on 2013-10-24
yup, C is largely about rolling out your own solutions to problems and that means a lot of boilerplate ;-)

In case of C++ STL's map (associative array) and vector (array) should take care of the data structure needs and simplify memory management.
C++ is in the same ballpark as C when it comes to performance. 11 lines are not going to happen but it should be manageable.
[http://en.wikipedia.org/wiki/Standard_Template_Library](http://en.wikipedia.org/wiki/Standard_Template_Library)

---

### Post by trent.josephsen on 2013-10-24
Here's how I might translate that original Perl snippet into C:
```
#define NUM_TORSIONS 20
char *torsions[NUM_TORSIONS] = {"alpha2", "alpha3", "alpha4", "beta2",
"beta3", "beta4", "gamma1", "gamma2", "gamma3", "gamma4", "epsilon1",
"epsilon2", "epsilon3", "zeta1", "zeta2", "zeta3", "chi1", "chi2", "chi3",
"chi4"};
dict_t *data = dict_from_keys(torsions);
for (int i = 0; i < NUM_TORSIONS; i++) {
	FILE *fh;
	(fh = fopen(torsions[i], "r"))
		|| log_exit("Cannot read %s", torsions[i]);
	while (!feof(fh)) {
		double temp;
		if (fscanf(fh, "%*f %lf", &temp) == 1) {
			dict_set(torsions[i],
				list_create_or_append(dict_get(torsions[i]), temp));
		}
	}
	fclose(fh);
}
```
Definitions of dict_t (which is a typdef), dict_from_keys, log_exit, dict_set, dict_get, and list_create_or_append are left as an exercise for the reader, but you can see how closely it matches the Perl and where I had to get a little verbose to do something in C that Perl does for you. Obviously for your real program you'd need additional functions to support the other stuff you need to do.

C++ would make this much easier, I'm sure. But Perl should be right speedy for I/O and text, so I would suggest just using Perl, if it's an option and you know how. If you really need C for performance in another part of the program, you could write a C library to do just that part, and then call it from Perl. Likely still less trouble than writing the whole thing in C.

(I'm assuming you're partial to Perl, or already have parts of this program written in Perl, but this applies equally well to other languages. As usual, your application will determine the best solution.)

---

### Post by hailholyghost on 2013-11-25
Hi everyone,

thanks very much for your very thoughtful replies.

IMHO, and I'm not a very experienced programmer, generally I can do C equivalents of Perl's hash structures with identically indexed arrays.

For example, if f(x,y) = z, then I can store all x values in a given array, where the nth index of each array matches one another.

Perl really isn't appropriate for this program.  The Perl equivalent took more than an hour to run.  The C program makes a lot of running averages, which perl doesn't seem to be very good with.

I will look into learning C++ though.  These Standard Template Libraries look very useful!

Much appreciated and a happy Thanksgiving!
-DC

---

### Post by r-senior on 2013-11-25
You might also consider GLIB, which has hash tables and dynamic arrays:

[https://developer.gnome.org/glib/stable/glib-Hash-Tables.html](https://developer.gnome.org/glib/stable/glib-Hash-Tables.html)
[https://developer.gnome.org/glib/stable/glib-Arrays.html](https://developer.gnome.org/glib/stable/glib-Arrays.html)

Complete set of GLIB data structures:

[https://developer.gnome.org/glib/stable/glib-data-types.html](https://developer.gnome.org/glib/stable/glib-data-types.html)

---

