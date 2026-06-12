---
title: "avl tree java issue"
date: 2009-03-30
forum: Programming Talk
---

### Post by adramalech on 2009-03-30
okay i am having some issues with an avl tree program here is my .java file with all the code...

```

import java.util.*;
import java.io.*;

public class AvlNode {
	
	public static int data, height;
	public static AvlNode root, right_child, left_child, current;
	
	public AvlNode(){
		root = null;
		current = root;
	}

	public AvlNode(int num){
		data = num;
		height = 0;
		right_child = null;
		left_child = null;
	}

	private static int balance(AvlNode current, AvlNode first_violation, AvlNode second_violation){
		AvlNode first = first_violation, second = second_violation;
		
		//checks to make sure that the children are not violating balance
		if(((current.left_child != null) && (current.right_child != null)) &&
		   ((current.left_child.height - current.right_child.height < 1) ||
		   (current.left_child.height - current.right_child.height > -1))){
			
			if(first == null){
				if(current.left_child.height - current.right_child.height > 1){
					return(balance(current, current.left_child, null));
				}
				else{
					return (balance(current, current.right_child, null));
				}
			}
			else if(second == null){//checking for the grandchild or second violation
				
				if((first.left_child.height - first.right_child.height) > 1){
					return(balance(current, first, first.left_child));
				}
				else if((first.left_child.height - first.right_child.height < -1)){
					return(balance(current, first, first.right_child));
				}
				else{//there is only one violation thus take the child with the greatest height
					if(first.left_child.height > first.right_child.height){
						return(balance(current, first, first.left_child));
					}
					else{
						return(balance(current, first, first.right_child));
					}
				}
			}
			else{//got the nodes referenced to, now evaluate rotations
				if((current.left_child.data == first.data) && //double rotation left
				   (first.left_child.data == second.data)){
					AvlNode left = first.left_child;
					first.left_child = left.right_child;
					left.right_child = first;
					first = left;
					
					//then change the heights of first and left
					first.height = adjust_height(first, first.height);
					left.height = adjust_height(left, left.height);
					return 0;
				}
				else if((current.right_child.data == first.data) && //single rotation left-right
						(first.left_child.data == second.data)){
					AvlNode left = first.left_child;
					AvlNode grandchild = left.right_child;
					left.right_child = grandchild.left_child;
					grandchild.left_child = left;
					first.left_child = grandchild.right_child;
					grandchild.right_child = first;
					first = grandchild;
					
					//adjust the heights of first and left nodes
					first.height = adjust_height(first, first.height);
					left.height = adjust_height(left, left.height);
					return 0;
				}
				else if((current.right_child.data == first.data) &&  //double rotation right
						(first.right_child.data == second.data)){
					AvlNode right = first.right_child;
					first.right_child = right.left_child;
					right.left_child = first;
					first = right;
					
					//changing heights for first and right nodes
					first.height = adjust_height(first, first.height);
					right.height = adjust_height(right, right.height);
					return 0;
				}
				else{ //single rotation right-left
					AvlNode right = first.right_child;
					AvlNode grandchild = right.left_child;
					right.left_child = grandchild.right_child;
					grandchild.right_child = right;
					first.right_child = grandchild.left_child;
					grandchild.left_child = first;
					first = grandchild;
					
					//adjust the heights of first and right nodes
					first.height = adjust_height(first, first.height);
					right.height = adjust_height(right, right.height);
					return 0;
				}
			}
		}
		else{
			return 0;//the tree is already balanced...thus do nothing.
		}
	}
		
	public static int insert(int num){
		if(root == null){
			root = new AvlNode(num);
			return 0;
		}
		else if(current == null){
			current = new AvlNode(num);
			balance(current, null, null);
			return 0;
		}
		else if(current.data > num){
			current = current.left_child;
			return(insert(num));
		}
		else{
			current = current.left_child;
			return(insert(num));
		}
	}
	
	public static int remove(int removeNum){
		if(current.data == removeNum){
			balance(root, null, null);
			current = null;
			return 0;
		}
		else if(current.data > removeNum){
			current = current.left_child;
			return (remove(removeNum));
		}
		else{
			current = current.right_child;
			return(remove(removeNum));
		}
	}
	
	public static AvlNode find(int num){
		//need to put some code here
		return current;
	}
	
	private static int adjust_height(AvlNode cur, int i){
		int num = i;
		
		if((cur.left_child == null) && cur.right_child == null){
			return num;
		}
		else if((cur.left_child == null) && (cur.right_child != null)){
			return adjust_height(cur.right_child, ++num);
		}
		else if((cur.left_child != null) && (cur.right_child == null)){
			return adjust_height(cur.right_child, ++num);
		}
		else{ //if cur has two children not null
			if(cur.left_child.height > cur.right_child.height){
				adjust_height(cur.left_child, ++num);
			}
			else{//right height is greater
				adjust_height(cur.right_child, ++num);
			}
			return num;
		}	
	}
	
	public static String toString(AvlNode node){
		String result = "";
		int i;
		if(node.height > 0){
			for(i = 0; i < node.height; i++){
				if((node.right_child != null) && (node.left_child != null)){
					result += " " + node.left_child.data + ", ";
					result += " " + node.data + ", ";
					result += " " + node.right_child.data + ", ";
					toString(node.right_child);
					toString(node.left_child);
				}
				else if((node.right_child != null) && (node.left_child == null)){
					result += " " + node.data + ", ";
					result += " " + node.right_child.data + ", ";
					toString(node.right_child);
				}
				else if((node.right_child == null) && (node.left_child != null)){
					result += " " + node.left_child.data + ", ";
					result += " " + node.data + ", ";
					toString(node.left_child);
				}
				else{//if the node is a leaf then just add that nodes data
					result += " " + node.data + ", ";
				}
			}
		}
		else{
			result += " " + node.data + " ";
		}
		return result;
	}
	
	public static void main(String [] argc) {
		int number = 0;
		String result = "";
		AvlNode found;
		
		//create the tree
		AvlNode tree = new AvlNode();
	
	        //create the keyboard buffer for console input
		Scanner keyboard = new Scanner(System.in);
		
		while(number != 5){
		    System.out.println("Please enter a number for the option you wish to select:\n" +
							   "\t1. Insert a number.\n" + "\t2. Remove a number.\n" +
							   "\t3. Print.\n" + "\t4. Find a number.\n" + "\t5. Quit.");
			number = keyboard.nextInt();
		
			while(number < 1 || number > 5){
				System.out.println("Please enter a number that correspondes to the correct option!\n" +
								   "\t1. Insert a number.\n" + "\t2. Remove a number.\n" +
								   "\t3. Print.\n" + "\t4. Find a number.\n" + "\t5. Quit.");
				number = keyboard.nextInt();
			}		
			switch(number){
				case 1: 
					System.out.println("Please enter a number you wish to insert: ");
					number = keyboard.nextInt();
					insert(number);
					break;
				case 2:
					System.out.println("Please enter a number you wish to remove: ");
					number = keyboard.nextInt();
					remove(number);
					break;
				case 3:
					result = toString(root);
					System.out.println(result);
					break;
				case 4:
					System.out.println("Please enter a number you wish to find: ");
					number = keyboard.nextInt();
					found = find(number);
					System.out.println("This is the position in the tree at which the number" +
									   " was found: " + found.data + " , with height, " + found.height);
					break;
				case 5:
					System.out.println("Have a good day!");
					break;
			}
		}
	}
}

```

okay so i converted the text book definition of traversals LL LR RL RR from the text book....but i am having issues with my toString method....and how to adjust the height after traversals....

if some one can give me some pointers that would be greatly appreciated...

*EDIT: okay so i have it to insert one node into the tree...and then print it out okay....but if i got to insert a second node into the tree it won't print out both of the them just one of them the newest one...

so if i inserted 1 then 2 then it will print 2...telling me that there is a problem with keeping track of the height of the tree else the adjust_height method is not working correctly

---

