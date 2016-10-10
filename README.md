<p align="center" >
<img src="https://raw.github.com/mhergon/RealmGeoQueries/assets/logo.png" alt="RealmGeoQueries" title="Logo" height=300>
</p>

![issues](https://img.shields.io/github/issues/mhergon/RealmGeoQueries.svg)
&emsp;
![stars](https://img.shields.io/github/stars/mhergon/RealmGeoQueries.svg)
&emsp;
![license](https://img.shields.io/badge/license-Apache%202.0-brightgreen.svg)

RealmGeoQueries simplifies spatial queries with [Realm Cocoa][1]. In the absence of and official functions, this library provide the possibility to do proximity search.
It's not necessary to include Geohash or other types of indexes in the model class as it only needs latitude and longitude properties.

## How To Get Started

### Installation with CocoaPods

```ruby
platform :ios, '9.0'
pod "RealmGeoQueries"
```

### Manually installation

[Download](https://github.com/mhergon/RealmGeoQueries/raw/master/GeoQueries.swift) (right-click) and add to your project.

### Requirements

| Version | Language  | Minimum iOS Target  |
|:--------------------:|:---------------------------:|:---------------------------:|
|          1.x         |            Swift            |            iOS 9            |

### Usage

First, import module;
```swift
import GeoQueries
```

Model must have a latitude and longitude keys, that have to be named "lat" and "lng" respectively. You can use another property names (use "latitudeKey" and "longitudeKey" parameters).

<br>
Search with MapView MKCoordinateRegion;
```swift
let results = try! Realm()
    .findInRegion(YourModelClass.self, region: mapView.region)
```
<br>

Search around the center with radius in meters;
```swift
let results = try! Realm()
    .findNearby(YourModelClass.self, origin: mapView.centerCoordinate, radius: 500, sortAscending: nil)
```
<br>

Filter Realm results with radius in meters;
```swift
let results = try! Realm()
    .objects(YourModelClass.self)
    .filter("type", "restaurant")
    .filterGeoRadius(mapView.centerCoordinate, radius: 500, sortAscending: nil)
```
<br>

See ```GeoQueries.swift``` for more options.

## Contact

- [Linkedin][2]
- [Twitter][3] (@mhergon)

[1]: http://www.realm.io
[2]: https://es.linkedin.com/in/marchervera
[3]: http://twitter.com/mhergon "Marc Hervera"

## License

Licensed under Apache License v2.0.
<br>
Copyright 2015 Marc Hervera.
