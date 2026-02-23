// Online C compiler to run C program online
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <stdbool.h>
#define max_size 100


typedef struct node
{
    int vertex;
    struct node* next;
}node;

typedef struct stack
{
    int arr[max_size];
    int top;
}stack;

void stackinit(stack* s)
{
    s->top = -1;
}

int isempty(stack* s)
{
    return (s->top == -1);
}

int isfull(stack* s)
{
    return (s->top == max_size-1);
}

void push(stack* s,int data)
{
    if (isfull(s)) return;
    
    s->arr[++(s->top)] = data;
}

int pop(stack* s)
{
    if (isempty(s)) return -99999;
    
    return s->arr[(s->top)--];
}

node* adjcent[max_size];

int main() {
    stack s;
    stackinit(&s);
    int vertexcount = 7;
    bool visited[vertexcount];
    memset(visited,0,sizeof(visited));
    memset(adjcent,0,sizeof(adjcent));
    
    int start = 0;
    
    int arc[][2] = {{0,1},{0,2},{1,3},{1,4},{2,5},{2,6}};
    
    for (int i=0;i<vertexcount-1;i++)
    {
        int dest = arc[i][1];
        int start = arc[i][0];
        node* newnode = (node*)malloc(sizeof(node));
        newnode->vertex = dest;
        newnode->next = adjcent[start];
        adjcent[start] = newnode;
        
        newnode = (node*)malloc(sizeof(node));
        newnode->vertex = start;
        newnode->next = adjcent[dest];
        adjcent[dest] = newnode;
    }

    push(&s,start);
    visited[start] = true;
    
    while (!isempty(&s))
    {
        int popdata = pop(&s);
        printf("%d ",popdata);
        node* ptr = adjcent[popdata];
        while (ptr)
        {
            if (visited[ptr->vertex])
            {
                ptr = ptr->next;
                continue;
            }
            
            push(&s,ptr->vertex);
            visited[ptr->vertex] = true;
            
            ptr = ptr->next;
        }
    }
}
