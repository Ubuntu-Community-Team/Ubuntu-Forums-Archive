---
title: "[Java] Code review for union-find data structure?"
date: 2012-01-29
forum: Programming Talk
---

### Post by skytreader on 2012-01-29
Hi. Can anyone comment on my code for a disjoint set data structure to implement union-find? As far as I'm aware, I got the basics down (with collapsing and weighting rules) but I'd like to see if there are further optimizations I can implement (or, if maybe, I'm mistaken that I got the basics down). I've run it with a few tests and I get the results I'm expecting, in any case. Thanks!

```

import java.util.Vector;

/**
 * Disjoint Set is basically a forest data structure used to implement the
 * union-find algorithm.
 */
public class DisjointSet<Sattelite> {
	
	private Vector<Integer> father;
	private Vector<Sattelite> data;

	/**
	 * Use this if you want to limit the cardinality of
	 * your set.
	 * 
	 * @param elements
	 */
	public DisjointSet(int elements) {
		father = new Vector<Integer>(elements);
		data = new Vector<Sattelite>(elements);
		for(int i = 0; i < elements; i++){
			father.set(i, -1);
		}
	}
	
	/**
	 * Use this for unlimited cardinality.
	 */
	public DisjointSet(){
		father = new Vector<Integer>();
		data = new Vector<Sattelite>();
	}

	/**
	 * Returns the index of the father of the given node. The value referenced
	 * by that index is less than zero. Negating this value returns
	 * the number of descendants of this father.
	 * 
	 * @param node
	 */
	private int findFather(int node) {
		int rovingNode = node;
		/*Find the root*/
		while (father.get(rovingNode) > 0) {
			rovingNode = father.get(rovingNode);
		}
		
		int compressRover = node;
		
		while(compressRover != rovingNode){
			int nextNode = father.get(compressRover);
			father.set(compressRover, rovingNode);
			compressRover = nextNode;
		}
		
		return rovingNode;
	}

	private void union(int i, int j) {
		int iFather = findFather(i);
		int jFather = findFather(j);
		
		int iChildren = father.get(iFather);
		int jChildren = father.get(jFather);
		int jointChildren = iChildren + jChildren;
		
		//-5 < -1
		if (iChildren < jChildren) {
			father.set(iFather,  jointChildren);
			father.set(jFather, iFather);
		} else{
			father.set(jFather, jointChildren);
			father.set(iFather, jFather);
		}
	}
	
	/**
	 * Make the father of node i and node j similar
	 * 
	 * @param i
	 * @param j
	 */
	public void union(Sattelite i, Sattelite j){
		//System.out.println("Union " + i.toString() + " " + j.toString());
		int iIndex = data.indexOf(i);
		int jIndex = data.indexOf(j);
		
		union(iIndex, jIndex);
	}
	
	/**
	 * Checks if the both data are under the same equivalence
	 * classes.
	 * @param i
	 * @param j
	 * @return
	 */
	public boolean isEqual(Sattelite i, Sattelite j){
		int iFather = findFather(data.indexOf(i));
		int jFather = findFather(data.indexOf(j));
		
		return iFather == jFather;
	}
	
	/**
	 * Adds the given data to the forest.
	 * @param s
	 */
	public void add(Sattelite s){
		data.add(s);
		father.add(-1);
	}
	
	/**
	 * Counts the number of distinct equivalence classes in this instance.
	 * @return
	 */
	public int countClasses(){
		int limit = father.size();
		int classCount = 0;
		
		for(int i = 0; i < limit; i++){
			if(father.get(i) <= 0){
				classCount += 1;
			}
		}
		
		return classCount;
	}
	
}


```

---

