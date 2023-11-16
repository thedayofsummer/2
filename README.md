tree 

import turtle
import random

# Set up the screen
screen = turtle.Screen()
screen.title("tree")
screen.bgcolor("white")

# Create a turtle for drawing
tree = turtle.Turtle()
#tree.hideturtle()
tree.speed(0)
tree.color("brown")
tree.width(2)

# Function to draw a branch of the tree
def draw_branch(branch_length, angle, leaf_chance):
    if branch_length > 5:
        tree.pensize(branch_length / 10)
        tree.forward(branch_length)
        tree.left(angle)
        draw_branch(branch_length - random.randint(10, 20), angle, leaf_chance)
        tree.right(angle * 2)
        draw_branch(branch_length - random.randint(10, 20), angle, leaf_chance)
        tree.left(angle)
        tree.backward(branch_length)
    else:
        # Draw leaves at the end of branches
        if random.randint(1, leaf_chance) == 1:
            draw_leaf()

# Function to draw a leaf at the end of a branch
def draw_leaf():
    leaf_size = random.randint(5, 15)
    tree.color("green")
    tree.dot(leaf_size)
    tree.color("brown")

# Move turtle to starting position
tree.left(90)
tree.penup()
tree.setpos(0, -250)
tree.pendown()

# Draw the trunk of the tree
tree.pensize(15)
tree.forward(60)

# Draw the branches of the tree
draw_branch(100, 30, 5)  # Adjust leaf_chance for leaf frequency

# Hide the turtle and display the result
tree.hideturtle()
turtle.done()
