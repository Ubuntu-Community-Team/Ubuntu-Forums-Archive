---
title: "Java: Programming problems need some help please"
date: 2006-10-24
forum: Programming Talk
---

### Post by Blacktalon on 2006-10-24
Hello everyone,
Before anyone asks yes this is for a project for school, but I have it 95% done and am having trouble with just two little errors my Eclipse keeps saying it doesn't like, and would like to see if anyone has any suggestions on how to get ride of them.


I have marked them in Blue.  I hope some knows where I went wrong, thanks for any help possible.

~BT


 * A file will give an input, this will probably require an i/o, and string tokenizer.
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.*;


public class BinPacking {
	private int _binCount;
	private int _numChecks;
    private int _bin[];
    private ArrayList _manyBins;
    private int MAX_SIZE;
    private int MAX_ITEMS;
    private int _items[];
    
    /**
     * Constructor method.
     * @param File
     * @throws FileNotFoundException
     */
    public BinPacking (int[] _tmpItems) throws FileNotFoundException, IOException{
  //   	StringTokenizer st = new StringTokenizer(File);
    	
    	
    	MAX_SIZE = _tmpItems[0];
    	_tmpItems[0] = 0;
    	MAX_ITEMS = _tmpItems[1];
    	_tmpItems[1] = 0;
    	int _bin[] = new int[MAX_SIZE];
    	int _items[] = new int[MAX_ITEMS];
    	for(int i =0; i < MAX_ITEMS; i++ ){
    		int j = 2;
    		_items[i] = _tmpItems[j];
    		j++;
    	}
    	ArrayList _manyBins = new ArrayList();
    	sort(_items);
    	packBin(0);
    	checkWeight();
    	
    }
    /**
     * Sort items into decending order
     * @params _items[]
     */
    public void sort(int _items[]){
    	int l = 0;
    	int r = l+1;
    	for(int i = l + 1; i <= r; i++){
            for(int j = i; j > l; j--){
        	   
        	   if(_items[j]< _items[j-1]){
        		  exch(_items,j,j-1);
        	   }
        	}
    	}
    }
    /**
     * The exch is where the values of _items is changed around if called upon.
     * @param _items, int i, int j
     */
    public void exch(int[] _items, int i, int j) {
		int t = _items[i];
		_items[i] = _items[j];
		_items[j] = t;
    }
    /**
     * hasSpace is to determine if the bin has space
     * @param int k, int c 
     * @return boolean
     */
    public boolean hasSpace(int k, int c) {
    	
    	_numChecks++;
    	System.out.println("\rnumChecks = " + _numChecks);
    	
    	if(_items[k]>MAX_SIZE){
    		System.out.print("FAILURE! Element way to large please change and try again! " +_items[k]);
    		System.exit(0);
    	}
    	
    	if(_manyBins.isEmpty() || _manyBins.get(c) == null){
    		_manyBins.add(_bin[MAX_SIZE]);
    		_binCount++;
    		System.out.println("\rbinCount = " +_binCount);
    	}
    	//check bin's for space by retriving their value
    	if(_items[k] > getBinValue(c)){
    		hasSpace(k, c+1);
    		return false;
    	}
    	    	 
    	return true;
    }
    /**
     * Gets the Bin Value.
     * @param i
     * @return
     */
    public int getBinValue(int i){
    	_manyBins.get(i);
    	int binValue=0;
    	for(int c = 0; c < _bin.length; c++){
    		binValue+=_bin[c];
    	}
    	
    	return binValue;
    }
    /**
     * packBin: this is where if a bin hasSpace then it will put it into other it recursively checks other bins, if non then new bin is created and binCount incremented by one
     * @param int k
     */
	public void packBin(int k){
		int i = 0;
		int x= 0;
		int j = 0;
		if(j<MAX_ITEMS){
			if (hasSpace(k, i)){
				j++;
				_bin[x]=_items[k];
				
		    }
			packBin(k++);
		}
		
	}
	/**
	 * toString this the toString that will print out the end results
	 */
/**	public void toString(String result){
		
	}
*/ 
	/**
	 * Check to for weight distrubution
	 */
	public void checkWeight(){
		int i =0;
		//find the last entry in the array list and check to see its size if its size is 1/3 of the maximum weight then add to it.
		if(getBinValue(_manyBins.size() - 1) <= (int)(MAX_SIZE / 3)){
			_manyBins.get(i);
			int tmpBin = _bin[_bin.length -1];
			if(hasSpace(tmpBin, i)){ 
			   _bin[_bin.length - 1] = 0;
			   _manyBins.get(_manyBins.size() - 1);
			   _bin[_bin.length] = tmpBin;
			   i++;
			   checkWeight();
			}
		}
	}
	/**
	 * Display all the bins and their contents.
	 */
	public void display(){
		for(int i = 0; i<_manyBins.size(); i++){
			System.out.print("**  Bin["+ i +"]: ");
			_manyBins.get(i);
			for(int j = 0; j < _bin.length; j++){
				System.out.println(" "+_bin[j] +"**");
			}
		}
		System.out.println("Total number of checks : "+ _numChecks);
		System.out.println("Total number of bins : "+_binCount);
	}

	
	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
		      [COLOR="Blue"]ArrayList<Integer> tmpItems = new ArrayList<Integer>();[/COLOR]
		      FileReader fr = new FileReader(args[0]);

		      int i;
		      
		      while ((i = fr.read()) != -1) {
		        char c = (char) i;
		        int k = c - '0';
		        if (k >= 0 && k < 10)
		          tmpItems.add(k);
		      }
		      int[] _tmpItems = new int[tmpItems.size()];
		        for (int j =0; j<tmpItems.size(); j++){
		        	_tmpItems[j] = Integer.parseInt(tmpItems.get(j));
		        }
		      
		fr.close();
		    } catch (Exception e) {
		      System.out.println("Exception: " + e);
		    }
		
		BinPacking bp = new BinPacking([COLOR="Blue"]_tmpItems)[/COLOR];
		System.out.println("******************************************************************");
		System.out.println("Success!!");
		bp.display();
		System.out.println("******************************************************************");
		
	}

}

---

### Post by yaaarrrgg on 2006-10-24
i did a quick edit so this would compile.  I didn't look over the program though to check for any logical errors:

```

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.*;


public class BinPacking {
    private int _binCount;
    private int _numChecks;
    private int _bin[];
    private ArrayList _manyBins;
    private int MAX_SIZE;
    private int MAX_ITEMS;
    private int _items[];

    /**
      * Constructor method.
      * @param File
      * @throws FileNotFoundException
      */
    public BinPacking (int[] _tmpItems) throws FileNotFoundException, IOException{
        // StringTokenizer st = new StringTokenizer(File);


        MAX_SIZE = _tmpItems[0];
        _tmpItems[0] = 0;
        MAX_ITEMS = _tmpItems[1];
        _tmpItems[1] = 0;
        int _bin[] = new int[MAX_SIZE];
        int _items[] = new int[MAX_ITEMS];
        for(int i =0; i < MAX_ITEMS; i++ ){
            int j = 2;
            _items[i] = _tmpItems[j];
            j++;
        }
        ArrayList _manyBins = new ArrayList();
        sort(_items);
        packBin(0);
        checkWeight();

    }
    /**
      * Sort items into decending order
      * @params _items[]
      */
    public void sort(int _items[]){
        int l = 0;
        int r = l+1;
        for(int i = l + 1; i <= r; i++){
            for(int j = i; j > l; j--){

                if(_items[j]< _items[j-1]){
                    exch(_items,j,j-1);
                }
            }
        }
    }
    /**
      * The exch is where the values of _items is changed around if called upon.
      * @param _items, int i, int j
      */
    public void exch(int[] _items, int i, int j) {
        int t = _items[i];
        _items[i] = _items[j];
        _items[j] = t;
    }
    /**
      * hasSpace is to determine if the bin has space
      * @param int k, int c
      * @return boolean
      */
    public boolean hasSpace(int k, int c) {

        _numChecks++;
        System.out.println("\rnumChecks = " + _numChecks);

        if(_items[k]>MAX_SIZE){
            System.out.print("FAILURE! Element way to large please change and try again! " +_items[k]);
            System.exit(0);
        }

        if(_manyBins.isEmpty() || _manyBins.get(c) == null){
            _manyBins.add(_bin[MAX_SIZE]);
            _binCount++;
            System.out.println("\rbinCount = " +_binCount);
        }
        //check bin's for space by retriving their value
        if(_items[k] > getBinValue(c)){
            hasSpace(k, c+1);
            return false;
        }

        return true;
    }
    /**
      * Gets the Bin Value.
      * @param i
      * @return
      */
    public int getBinValue(int i){
        _manyBins.get(i);
        int binValue=0;
        for(int c = 0; c < _bin.length; c++){
            binValue+=_bin[c];
        }

        return binValue;
    }
    /**
      * packBin: this is where if a bin hasSpace then it will put it into other it recursively checks other bins, if non then new bin is created and binCount incremented by one
      * @param int k
      */
    public void packBin(int k){
        int i = 0;
        int x= 0;
        int j = 0;
        if(j<MAX_ITEMS){
            if (hasSpace(k, i)){
                j++;
                _bin[x]=_items[k];

            }
            packBin(k++);
        }

    }
    /**
      * toString this the toString that will print out the end results
      */
    /** public void toString(String result){

      }
      */
    /**
      * Check to for weight distrubution
      */
    public void checkWeight(){
        int i =0;
        //find the last entry in the array list and check to see its size if its size is 1/3 of the maximum weight then add to it.
        if(getBinValue(_manyBins.size() - 1) <= (int)(MAX_SIZE / 3)){
            _manyBins.get(i);
            int tmpBin = _bin[_bin.length -1];
            if(hasSpace(tmpBin, i)){
                _bin[_bin.length - 1] = 0;
                _manyBins.get(_manyBins.size() - 1);
                _bin[_bin.length] = tmpBin;
                i++;
                checkWeight();
            }
        }
    }
    /**
      * Display all the bins and their contents.
      */
    public void display(){
        for(int i = 0; i<_manyBins.size(); i++){
            System.out.print("** Bin["+ i +"]: ");
            _manyBins.get(i);
            for(int j = 0; j < _bin.length; j++){
                System.out.println(" "+_bin[j] +"**");
            }
        }
        System.out.println("Total number of checks : "+ _numChecks);
        System.out.println("Total number of bins : "+_binCount);
    }


    /**
      * @param args
      */
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        try {
            ArrayList<Integer> tmpItems = new ArrayList<Integer>();
            FileReader fr = new FileReader(args[0]);

            int i;

            while ((i = fr.read()) != -1) {
                char c = (char) i;
                int k = c - '0';
                if (k >= 0 && k < 10)
                    tmpItems.add(k);
            }
            int[] _tmpItems = new int[tmpItems.size()];
            for (int j =0; j<tmpItems.size(); j++){
                //_tmpItems[j] = Integer.parseInt(tmpItems.get(j));
                _tmpItems[j] = tmpItems.get(j);
            }

            fr.close();
       
            // _tmpItems not defined outside try block 
            BinPacking bp = new BinPacking(_tmpItems);
            System.out.println("****************************** ************************************");
            System.out.println("Success!!");
            bp.display();
            System.out.println("****************************** ************************************");

        } catch (Exception e) {
            System.out.println("Exception: " + e);
        }

        //moved block
   
    }

}

```

---

### Post by Blacktalon on 2006-10-24
Getting it to complie is still a good thing, thank you very much.

---

### Post by DeadEyes on 2006-10-25
Your brackets don't seem to match up in main or is that just a typo?
What is the error for the ArrayList declaration?
Are you using Java 5?

---

### Post by Blacktalon on 2006-10-25
I just recounted them they all seem to match up, I can get it complie ok, but I am now getting an problem with the ArrayList<Integer>, saying that it can't cast an Generic type Integer.  Which I know it's lieing about not being able to cast Generic's cause I have done it with my battleship game from the head first book which does cast and Generic String.  Anyways, but yeah I am running Java 5.

I figure if I can't get this resolved soon I'm gonna have to do the stupid trick that I hate doing, as in using my array and setting the max size to like ten, and when it needs to acceed that to create a new array with twice the length of the old one and have everything put into the new one, and etc.  But if anyone can come up with a solution to my ArrayList problem I would greatly appreciate it.

Thanks,
~BT

---

### Post by amo-ej1 on 2006-10-26
Just to be checking which jdk are you using ? How does java -version look ? Are you using the sun jdk or gcj ?

---

### Post by dxxvi on 2006-10-26
Thanks for making a more readable code. I don't see you ArrayList problem. Could you be more specific? BTW, FileNotFoundException extends IOException, so if your method throws IOException, you don't need to make it throw FileNotFoundException, I think.

---

### Post by SlCKB0Y on 2006-10-26
Firstly. That is terrible coding with some terrible stuff in there. 

In your main method, why are you reading from a file, putting it in an ArrayList, and then taking it out and putting it in an array? Thats totally unecessary. Use one or the other. 

You might consider in future...

1. Using some comments.
2. Using better variable names and method names
3. Reducing code by using helper methods
4. Compiling your code more often. This should never happen. You should not add more than a few lines of code at a time without compiling.

---

### Post by yaaarrrgg on 2006-10-26
I looked over the code a little.  Here's a couple things that don't look right to me.  note, i'm not sure what type of file you are working with, or what the program is supposed to be doing.

You read in the file into an array, one char at a time, and discard some chars:

```

            while ((i = fr.read()) != -1) {
                char c = (char) i;
                // probably not what you want
                int k = c - '0';
                // discard some data
                if (k >= 0 && k < 10)
                    tmpItems.add(k);
            }
            int[] _tmpItems = new int[tmpItems.size()];
            for (int j =0; j<tmpItems.size(); j++){
                //_tmpItems[j] = Integer.parseInt(tmpItems.get(j));
                _tmpItems[j] = tmpItems.get(j);
            }

```

but then you use data from the file to set the array size (note that your ints are < 10 ... is that right?)  This means your arrays' size can never be greater than 10.

```

        MAX_SIZE = _tmpItems[0];
        _tmpItems[0] = 0;
        MAX_ITEMS = _tmpItems[1];
        _tmpItems[1] = 0;

```

Also, you are using chars, but converting some to ints between 0 and 9.  I'm not sure this is doing what you want.  

Are you tring to convert numeric text to an int?  If so, this won't work at all.  You'll need to parse a block of chars into a string (for example, using Scanner or StringTokenizer), and then use Integer.parseInt(String).

then you define some arrays:

```

        int _bin[] = new int[MAX_SIZE];
        int _items[] = new int[MAX_ITEMS];

```

using "int" this means this is defined locally in the function, and disapears when the function returns.  You also have an array with the same name defined at the class scope.  It's never set, but the method hasSpace(int k, int c) is referring to it.

Edit: on a general note, it seems like there is some redundant array shuffling and loops in there.  at most, i think you need two arrays: a source and desitnation.

---

### Post by chadmichael on 2006-10-26
Don't take this the wrong way.  But if you really want to learn, I would recommend not using eclipse.  It hides a lot of things that are key to really becoming a good developer.  It will be well worth the effort in the long run.  Your in school to learn, right?

---

### Post by shining on 2006-10-26
> **chadmichael said:**
> Don't take this the wrong way.  But if you really want to learn, I would recommend not using eclipse.  It hides a lot of things that are key to really becoming a good developer.  It will be well worth the effort in the long run.  Your in school to learn, right?

Our teachers actually asked us to learn to use an IDE, like netbeans or eclipse.
There is also a learning process before starting to benefit from an IDE, so I believe the same could be said for IDE: it will be well worth the effort in the long run.
And I don't think using an IDE necessarily means being a bad developer. When used right, I would think you can benefit from the features providen for writing code of the same quality faster.

That said, I also enjoy using xemacs or vim, without using any special features (only indent and syntax highlighting) but I only write very small and trivial programs, never more than a few hundred loc.

---

### Post by Blacktalon on 2006-10-26
I ended up fixing up my code a bit and got rid of the arraylist but now i just end up getting an ArrayIndexOutOfBoundException.  And I am going to talk to my professor about, cause this the way I really hate coding for integers to go into an array.

Oh and chadmichael, dude, if I had my way I would cutt up Eclipse, dunk it in acid, burn it, and send it to hell!!  I personally don't like using it for Java, but It is an REQUIREMENT to be used in my Computer Science class, otherwise I would agree and say don't use it.  In all I just want to make you aware that I am not choosing to use it, I am basically forced to use it or recieve an 'F'.  And I please don't say, how can he tell, its easy cause when saving an file in elcipse it's freakishly huge.

---

