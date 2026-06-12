---
title: "Help using python multiprocessing for edit distance calculation"
date: 2013-07-16
forum: Programming Talk
---

### Post by edm1 on 2013-07-16
I first started learning programming about a year ago as part of my masters so I'd say I have a good intermediate knowledge of python and I'm just trying to get to grips with some of the more advanced features that will be useful for me.

I study bioninformatics so a lot of what I do is crunching massive amounts of data. I have used the multiprocessing library in python to run parallel instances of an external program (BLAST) through subprocess and that all works fine. However I can't work out where to start if I want to run a function in my script in parallel.

Basically, what I am trying to do is calculate the edit distance between each sequence in a list of ~15,000 length using the python-Levenshtein c-module. Any pointers in the right direction would be a great help. The function where multiprocessing will be used is shown below but it is just really the distance() function that needs to be done in parallel.

At the moment I am calculating the edit distance and evaluating it for each pair at a time but I assume I need to calculate distances all at once, saving the results to a dictionary. I'm not even sure if the multiprocessing module would be the right thing for what I am trying to do. Thanks.

```
def cluster(record_list, cluster_threshold, auto_merge_dist):
    """Takes a list of records in decesending group size order and clusters 
       them according to similarity (caluclated using edit distance). 
       
       If the distance between two sequences is < auto_merge_dist the 
       sequences will be merged irrespective of the size differences 
       between them.
       
       However if the distance is > auto_merge_dist, then merging will only 
       occur if merge_function retruns True.
       
       Return: A dictionary entry for each cluster, containing a list of 
       records that make up the cluster.
    """
    # Initiate variables
    total_records = len(record_list)
    merged = set([])
    clusters = {}
    
    while len(record_list) > 0:
        centroid = record_list[0]
        # Print progress to stdout
        if len(record_list)%20 == 0:
            print_progress(len(merged), total_records)
        # Continue if the centroid has already been merged
        if centroid.id in merged:
            del record_list[0]
            continue
        # Make new entry in clusters dict and add centroid id to merged set
        clusters[centroid.id] = [centroid]
        merged.add(centroid.id)
        # Iterate through all other records
        for target in record_list[1:]:
            # Continue if target has already been merged
            if target.id in merged:
                continue
            # Calculate distance between centroid and target
            dist = distance(str(centroid.seq),str(target.seq))
            # Merge clusters if dist < auto_merge_dist or id merge_finction
            # returns True.
            if dist <= auto_merge_dist or \
                    merge_function(cluster_threshold, dist,
                                   centroid.annotations['size'],
                                   target.annotations['size']):
                clusters[centroid.id].append(target)
                merged.add(target.id)
        del record_list[0]
        
    print_progress(total_records,total_records)
    print
    
    # Make reference dict with pointers from reads to cluster centroid
    cluster_refs = {}
    for centroid_id in clusters:
        for target in clusters[centroid_id]:
            cluster_refs[target.id] = centroid_id
    
    return clusters, cluster_refs
```

---

### Post by Erdaron on 2013-07-16
I do simulations in quantum optics, and multiprocessing has been wonderful. An easy way to set it up:
```
import multiprocessing
pool = multiprocessing.Pool()
results = pool.map_async(distance, prmque).get()
pool.close()
pool.join()
del pool
```

Where prmque is an iterable containing function inputs (it's very similar to the built-in map() function), for example a list of object pairs. The only catch is that the map() and map_async() methods of the Pool() object can only handle a single variable to pass to the function. They cannot perform any unpacking.

map_async() is faster than map() if calculations take vastly varying times (which is the case for me). For you, each calculation might take a nearly identical amount of time, so using pool.map() is probably easier.

Setting up and closing a Pool() object takes time, so it's useful to just set it up once and reuse it with each iteration.

---

