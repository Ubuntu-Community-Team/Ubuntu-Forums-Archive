---
title: "instantiating an array of objects with constructors in java"
date: 2008-12-24
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-12-24
hi so i have my class square with a constructor...i want to pass different vaules into each one when i instantiate it...but after i declare the array how do i do this?

in C# it was someting along the lines of

```

squares[i] = new Square(25, 75, 50 50);

```

but i dont think that that is the case of java

---

### Post by s3gfault on 2008-12-24
I'm no expert in java, but i think that does work.  The key is to have the array declared properly first
```

Square squares[] = new Square[NUM_OF_SQUARES];
squares[0] = new Square(12, 13, 14,15);

```

---

### Post by Reiger on 2008-12-24
IIRC the proper syntax is:
```

Square [] squares=new Square [] {
      new Square(11),
      new Square(12),
      /* more constructor calling */
      new Square(15)
    };

```

Or equivalently:
```

int i, num_squares = NUM_OF_SQUARES;
Square [] squares = new Square [num_squares];
for(i=0;i<squares.length;i++) {
  /* code which calculates params */
  squares[i]=new Square(/* [result of code which calculate params] */);
}

```

EDIT: And this is assuming you have a public constructor Square(int) available; tailor the code to meet your needs.

---

### Post by shadylookin on 2008-12-25
> **jimi_hendrix said:**
> hi so i have my class square with a constructor...i want to pass different vaules into each one when i instantiate it...but after i declare the array how do i do this?

in C# it was someting along the lines of

```

squares[i] = new Square(25, 75, 50 50);

```

but i dont think that that is the case of java

that's correct but if you try accessing an index that you haven't specifically initialized then you'll get a null pointer exception

for instance 

[PHP]
public class SquareUser {
	public static void main(String args[]) {
		Square[] squares = new Square[100];
		squares[10].getX();
	}

}

[/PHP]

will return a null pointer exception because you haven't specifically initialized squares at index 10.

if however you do

[PHP]public class SquareUser {
	public static void main(String args[]) {
		Square[] squares = new Square[100];
                squares[10] = new Square(18);
		squares[10].getX();
	}

}
[/PHP]

it will work


For this reason I honestly prefer using the java.util.List when I'm using objects because then you won't have indexes that hold nothing and throw null pointer exceptions when you accidentally use them
[PHP]
import java.util.List;
import java.util.ArrayList;

public class SquareUser {
	public static void main(String args[]) {
		List<Square> squares = new ArrayList<Square>();
		squares.add(new Square(10));
		System.out.println(squares.get(0).getX());
	}

}
[/PHP]

---

