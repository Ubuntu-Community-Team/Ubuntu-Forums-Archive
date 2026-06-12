---
title: "Error: Dereferencing pointer to incomplete type (?)"
date: 2010-01-15
forum: Programming Talk
---

### Post by tom66 on 2010-01-15
I am getting errors with GCC trying to compile this:

```

void way_update_bbox(struct Way *way, struct Node *node)
{
    /* Updates the bbox of the way. Doesn't reevaluate all the nodes;
     * instead, it checks to see if the passed node is outside of the
     * current way's bbox. */
    if(!bbox_in_test(&way->bbox, node->pos)) {
        // Is the point outside of the top left of the rectangle?
        if(way->bbox.tl.lat > node->pos.lat || way->bbox.tl.lon > node->pos.lon) {
            way->bbox.tl.lat = node->pos.lat;
            way->bbox.tl.lon = node->pos.lon;
            return;
        }
        // Is the point outside of the bottom right of the rectangle?
        if(way->bbox.br.lat < node->pos.lat || way->bbox.br.lon < node->pos.lon) {
            way->bbox.br.lat = node->pos.lat;
            way->bbox.br.lon = node->pos.lon;
            return;
        }
    }
}

```

with the definitions for position.h here:

```

#pragma once
#define DIV_DOUBLE(a, b) ((double)(a) / (double)(b))
#define DEG_2_RAD(x) (x * 0.0174532925)

struct Position2D
{
    // Latitude & longitude stored as unsigned values 0 - 2^32-1.
    // This is accurate to seven and a half decimal places when 
    // translated into lat/lon.
    unsigned int lat, lon;  
};

struct Position2DBBox
{
    // Bounding box with top left and bottom left positions.
    struct Position2D tl;
    struct Position2D br;
};

void position_to_lat_lon(struct Position2D *, double *, double *);
void lat_lon_to_position(struct Position2D *, double, double);
double position_distance(struct Position2D *, struct Position2D *);
int position_quick_distance(struct Position2D *, struct Position2D *);
double position_accurate_distance(struct Position2D *, struct Position2D *);

int bbox_in_test(struct Position2DBBox *, struct Position2D *);

```

and for node.h:

```

#pragma once
#include "position.h"
#include "way.h"
#include "tags.h"

struct MapNode
{
    int numWays;
    struct MapWay **ways;   // Ways this node belongs to.
    struct Position2D pos;  // Lat, Lon position.
    struct Tag *head_tag;
};

```

and for way.h:

```

#pragma once
#include "node.h"
#include "tags.h"

struct Node;

struct Way
{
    int numNodes;
    struct Node **nodes;
    struct Tag *head_tag;
    struct Position2DBBox bbox;
};

void way_add_node(struct Way *way, struct Node *node);

```

The errors are:

```

In file included from test.c:3:
node.c: In function ‘node_find_new’:
node.c:29: warning: unused variable ‘n’
node.c:29: warning: unused variable ‘i’
node.c:28: warning: unused variable ‘node’
In file included from test.c:4:
way.c: In function ‘way_update_bbox’:
way.c:19: error: dereferencing pointer to incomplete type
way.c:21: error: dereferencing pointer to incomplete type
way.c:21: error: dereferencing pointer to incomplete type
way.c:22: error: dereferencing pointer to incomplete type
way.c:23: error: dereferencing pointer to incomplete type
way.c:27: error: dereferencing pointer to incomplete type
way.c:27: error: dereferencing pointer to incomplete type
way.c:28: error: dereferencing pointer to incomplete type
way.c:29: error: dereferencing pointer to incomplete type

```

I don't know what I am doing wrong. I suspect it may have something to do with forward declarations of structures, but I wouldn't know how to fix it.

---

### Post by tom66 on 2010-01-15
Never mind, I just fixed my problem! Turns out that I had forward declared 'Node' instead of 'MapNode'; the compiler didn't know anything about 'MapNode' and kept trying to reference 'Node'.

---

