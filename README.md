# jsoni18n

IT'S NOT AVAILABLE IN HAXELIB YET. Soon.

An agnostic internationalization library working with JSON files in Haxe.

Agnostic?

* Translations files don't need to be in a specific location.
* It can work with or without OpenFL.

## Installation

In a shell, execute:

```
haxelib install jsoni18n
```

If you use a Project.xml, add:

```
<haxelib name="jsoni18n" />
```

If you use the haxe command and its flags, add:

```
haxe -lib jsoni18n ...
```

## Usage

### JSON files

It's JSON, objects and strings:

```json
{
  "welcome": {
    "hello": "Hoy!",
    "subtitle": "Welcome, :name!",
    "content": {
      "main": "Main content should be longer but it's boring.",
      "side": "Some useful side notes to shine in society."
    }
  },
  "secret": {
    "intro": "It's a secret page! Do you have authorization?"
  }
}
```

### Basics

There's only one import:

```haxe
import jsoni18n.I18n;
```

For the following examples, we assume you do something like this:

```haxe
// it could be Reg.lang or Context.userLang or App.currentLanguage ...
var lang : String = myGetCurrentLanguage();
```

If you use OpenFL, you can load a file:

```haxe
I18n.loadFromFile("assets/data/i18n_" + lang + ".json");
```

Or/else directly from a string:

```haxe
var jsonFileContent : String = myLangFileLoader();
I18n.loadFromString(jsonFileContent);
```

Now, to translate something:

```haxe
var hello : String = I18n.tr("welcome/hello");
```

### Prefix

You can add prefixes to keys from all data fetched by a loadFromFile() or loadFromString() like this:

```haxe
I18n.loadFromString(data, "ui/");
I18n.tr("ui/welcome/hello"); // Hoy!
```

### Variables

You can pass variables to strings returned by tr() like this:

```haxe
I18n.tr("welcome/subtitle", [ "name" => "Nekith" ]); // Welcome, Nekith!
```

### Configuration

Default depth delimiter is "/". You can change it like this:

```haxe
I18n.depthDelimiter = "_";
```

Default variable prefix is ":". You can change it like this:

```haxe
I18n.varPrefix = "@";
```

Coming: set the depth separator.

## License

New-BSD licensed. See LICENSE file.