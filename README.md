# OfflineMapsTileProvider
This project provides zip files of Tiles based on bbox Values. These files can be rendered in Native Android Application Using OSMDroid. We need to use gradle version less than 5.5 to build the project.


## Why would you want to use this?
Caching tiles for offline/disconnect use


## What sources can I use with this?
Any map source (baring legal issues) that uses the Z/X/Y tile naming convention.

## What output files can this produce?

Osmdroid style zip, sqlite and GEMFile databases.
Copy the output file to /sdcard/osmdroid/. Then use Osmdroid to render.

## How do I use this?

1.After building the project with gradle version less than 5.5
2.Navigate to build/libs/
3.Open a command line/terminal/bash shell

`java -jar osmdroid-packager-<VERSION>-jar-with-dependencies.jar -u url -ismap false -t <MapSourceName> -d <outputfile.zip> -zmin <MIN ZOOM> -zmax <MAX ZOOM up to 22> -n <NORTH> -s <SOUTH> -e <EAST> -w <WEST> -nthreads <optional, number of current threads, default 2> -fa <optional file extension add on, not really needed>1`

All bounds are in decimal degrees latitude/longitude.


## Important note

Here's a few usage examples. There's a few caveats that you must follow if you want these tiles to show up in OsmDroid.

1) The temporary folder to save files should be named the name of your map source.
2) In OsmDroid, set the map source's name equal to the temporary folder name.

`java -jar ....-jar -t <name of map source here> -d outputfile`

Example: Open Streem Map tiles (Mapnik)

````
java -jar ....jar -u http://b.tile.openstreetmap.org/%d/%d/%d.png -t Mapnik -d at_mapnik_13.zip -zmax 13 -n 49.03942 -s 46.40162 -e 17.14736 -w 9.44595
                                                                       ^ that's the important part!
````

## More reading

https://github.com/osmdroid/osmdroid/wiki/Offline-Map-Tiles

https://github.com/osmdroid/osmdroid/wiki/Map-Sources

