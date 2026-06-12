---
title: "Parameter/Argument Method Passing Question"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by mconway0003 on 2008-11-12
Hello,
I have a method:



    ```
  	public Cube(String id, String faceValues){
    		this.id = id;
    		id.toUpperCase();
    		for (int i =0; i <6; i++){
    			faces[i]=faceValues.charAt(i);
    		}
    		faceIndex = 0;
    		rnd = new Random(0);
     
    	}  

```


What I'm trying to do is obtain input from the user and set their input as the 'String id' parameter in the above Cube(String id, String faceValues) method:

  
```

     import java.util.Scanner;
    public class CubeTester {
    	//Instance variables
    	private Cube c1;
    	private Cube c2;
    	private Cube c3;
    	public static void main(String[] args) {
    		Scanner scan = new Scanner(System.in);
    		//Constructor 
    		Cube c1 = new Cube();
    		Cube c2 = new Cube();
    		Cube c3 = new Cube();
    		//Ask for String id
    		System.out.println("Enter cube id: ");
    		scan.next(); // I want to set this as String id in the Cube method
    		//Then ask for the String faceValue 
    		System.out.println("Enter 6 letters for faces of the cube: ");
    		scan.next(); //I want to set this a the String faceValue in the Cube method
    	}
    }   
```

Any help would be greatly appreciated.

Thanks

---

### Post by dhtseany on 2008-11-12
Programming Forums ;)

---

