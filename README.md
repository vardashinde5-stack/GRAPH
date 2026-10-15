# Experiment No. 9

## Title

**Backtracking: Graph Coloring Problem**

## Aim

To implement the Graph Coloring Problem using the Backtracking technique and analyze its time and space complexity.

## Program

```c
#include <stdio.h>

#define MAX 20

int graph[MAX][MAX];
int color[MAX];
int V, m;

int isSafe(int v, int c)
{
    for (int i = 0; i < V; i++)
    {
        if (graph[v][i] == 1 && color[i] == c)
            return 0;
    }

    return 1;
}

int graphColoring(int v)
{
    if (v == V)
        return 1;

    for (int c = 1; c <= m; c++)
    {
        if (isSafe(v, c))
        {
            color[v] = c;

            if (graphColoring(v + 1))
                return 1;

            // Backtrack
            color[v] = 0;
        }
    }

    return 0;
}

int main()
{
    printf("Enter number of vertices: ");
    scanf("%d", &V);

    printf("Enter number of colors: ");
    scanf("%d", &m);

    printf("Enter adjacency matrix:\n");

    for (int i = 0; i < V; i++)
    {
        for (int j = 0; j < V; j++)
        {
            scanf("%d", &graph[i][j]);
        }
    }

    for (int i = 0; i < V; i++)
    {
        color[i] = 0;
    }

    if (graphColoring(0))
    {
        printf("\nVertex\tColor\n");

        for (int i = 0; i < V; i++)
        {
            printf("%d\t%d\n", i, color[i]);
        }
    }
    else
    {
        printf("No valid coloring exists with %d colors.\n", m);
    }

    return 0;
}
```

## Output

The terminal output of the Graph Coloring Problem is shown below.

**Sample Input:**

```text
Enter number of vertices: 4
Enter number of colors: 3
Enter adjacency matrix:
0 1 1 1
1 0 1 0
1 1 0 1
1 0 1 0
```

**Sample Output:**

```text
Vertex  Color
0       1
1       2
2       3
3       2
```

**Note:** This is a sample output. You can replace it with a screenshot of your actual terminal output.

## Algorithm

1. Start the program.
2. Read the number of vertices and the number of available colors.
3. Read the adjacency matrix representing the graph.
4. Initialize the color of every vertex to zero.
5. Start coloring the graph from the first vertex.
6. Try assigning each available color to the current vertex.
7. Check whether any adjacent vertex already has the selected color.
8. If the color is safe, assign it to the current vertex.
9. Recursively attempt to color the next vertex.
10. If no color works for a vertex, remove the previously assigned color and try another color. This process is called **Backtracking**.
11. If all vertices are colored successfully, display the assigned colors.
12. Otherwise, display that no valid coloring exists with the given number of colors.
13. Stop the program.

## Time Complexity

| **Operation**                        | **Time Complexity**          |
| ------------------------------------ | ---------------------------- |
| Reading the adjacency matrix         | **O(V²)**                    |
| Initializing the color array         | **O(V)**                     |
| Checking whether a color is safe     | **O(V)**                     |
| Exploring possible color assignments | **O(m^V)** (upper bound)     |
| Overall Time Complexity              | **O(V × m^V)** (upper bound) |

### Explanation

The Graph Coloring Problem is solved using Backtracking by assigning colors to vertices while ensuring that no two adjacent vertices have the same color.

* Reading the adjacency matrix takes **O(V²)** time.
* The `isSafe()` function checks all vertices and takes **O(V)** time.
* Each vertex can potentially be assigned one of **m** colors.
* In the worst case, the algorithm explores up to **m^V** color assignments.
* Checking whether each assignment is safe adds a factor of **O(V)**.

Therefore:

**Time Complexity = O(V × m^V)** (worst-case upper bound).

Where:

* **V** = Number of vertices.
* **m** = Number of available colors.

## Space Complexity

The program uses the following data structures:

* `graph[MAX][MAX]` to store the adjacency matrix.
* `color[MAX]` to store the color assigned to each vertex.
* Recursive function calls to explore possible color assignments.

The adjacency matrix requires **O(V²)** space, while the color array and recursion stack each require **O(V)** space.

Therefore:

**Space Complexity = O(V²)**.

## Applications

1. Coloring maps so that adjacent regions have different colors.
2. Allocating frequencies in wireless communication networks.
3. Register allocation in compilers.
4. Scheduling tasks that cannot occur simultaneously.
5. Solving constraint-satisfaction problems.
6. Assigning resources while avoiding conflicts.

## Advantages

* Provides a systematic method for finding a valid graph coloring.
* Ensures that adjacent vertices receive different colors.
* Uses Backtracking to abandon invalid color assignments.
* Can determine whether a graph is colorable using a specified number of colors.
* Demonstrates the application of recursion and constraint checking.

## Limitations

* The number of possible color assignments grows exponentially with the number of vertices.
* The algorithm can become slow for large graphs.
* The given implementation uses a fixed maximum of 20 vertices.
* The program finds one valid coloring rather than listing all possible colorings.
* The result depends on the number of colors provided.

## Conclusion

The Graph Coloring Problem is solved using the **Backtracking technique** by assigning colors to graph vertices while ensuring that no two adjacent vertices share the same color.

The algorithm recursively assigns colors, checks constraints, and backtracks whenever a conflict occurs.

For the given implementation, the worst-case time complexity is **O(V × m^V)**, and the space complexity is **O(V²)**.

This experiment demonstrates how Backtracking can solve graph-based constraint problems by exploring possible solutions and rejecting invalid assignments.
 OUTPUT IMAGE <img width="1312" height="1199" alt="GRAPH" src="https://github.com/user-attachments/assets/3c574545-b5bb-4067-a6d2-36f180fe15ee" />
