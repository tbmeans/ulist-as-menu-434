# Rendering a menu from an unordered list
This is designed mobile first, showing submenus between lines of the parent
menu. The component expects to receive, for its main prop "list" arrays of
child node pairs for each list item element, a child to display menu text and
an optional second child node storing a submenu.

## Props

### list
An array of items, each item itself an array containing text for the menu item
heading/name and an optional object for a submenu under that heading, such as
another ListAsMenu component recursively generated.

### path
A representation of menu clickthrough as a string sequence of single-digit
indices--no more than 10 items per menu--each the index of a selected list
item to progress through levels of submenus, e.g. 1st index is a choice from
the main menu in order to display the first submenu.

### pathLength
The number of path indices required to view the given list

### setPath
With clickthru path indices as a part of state higher in the app hierarchy,
assign this prop the setter of path state from its hook or just setState.bind.

### isLeaf
This prop takes a function that returns true if a path indices sequence reaches
a leaf node of the menu, i.e. completes a menu choice as opposed to just
opening a submenu.
Best to arrange your menu structure to make it as easy as possible to write such
a function, for example, the function is just based on particulars of a menu
instead of abstractions or tree traversal.

### values
An array of values selectable from a submenu for the given non-leaf path

### setValue
An array of state setters for each category of values that the menu deals with,
such as a map of each main menu heading to the setter of a value related to
the heading

### unlocked
A string of bits, each bit of index i in the string indicating whether main
menu heading index i (in an array of headings such as one made by Object.keys
of a menu text object) is operable to select a value or open a submenu, 1 for
operable, 0 for inoperable.

