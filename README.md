## Installation

  1. Install this plugin through the Asset Library in Godot or paste the contents of this repository to your projects folder.
  
  2. Activate the plugin in Godot through the project settings
 
## Instructions
  When the plugin is activated, a singleton named "NodeFinder" is added to the editor. You must call functions through this singleton.
```GDScript
  NodeFinder.example_function()
```
If you think "NodeFinder" is too long and you want it to be something shorter like "NF", you can change the string in the plugin.gd. Just make sure to disable the plugin beforehand!


## Methods
  There are two ways to access nodes through this singleton. 
You can either register nodes with a key, which essentially makes the singleton work like a global dictionary.
Or you can simply search for a node by its name. Only the nodes that belong to the current scene the function is being called from
are accessible!

```gdscript
  NodeFinder.get_named(nodename: String, suppress: bool = false `optional`)
```
  This function will find the node with the given name. If more than one node exists in the scene with that name,
  it will return an array that contains all those nodes. This will cause the plugin to give out a warning about it.
  If you give the second argument as `true` it will suppress that warning.
 
 ---

```gdscript
  NodeFinder.register( key: String, node: Node )
```
  Registers this node under this key. If the key has been registered before, it will push a warning.
  
---

```gdscript
  NodeFinder.get( key: String, suppress: bool = false `optional`)
```
  Retrieves the node that is registered to this key. Pushes a warning if key doesn't exist. If the key has been found in 
  multiple registeries for any reason, it will return an array which contains all those nodes instead.
  
---

```gdscript
  NodeFinder.override( key: String, node: Node )
```
  Registers this node under this key. If the key has been registered before, it will override.
 
---

```gdscript
  NodeFinder.unregister( key: String, root: Node = null `optional`)
```
  Removes the registry of that key. This might push a warning if the same key has been used in different scenes. In which case
  you should provide the root of the scene that holds the node you wish to delete.

