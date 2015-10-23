
The [OpenStreetMap](http://www.openstreetmap.org/) project started in 2004, and as of 10/2015, the project contains slightly more than 3 billion map elements with approximately 1 million entries added per day, see the [OSM wiki](http://wiki.openstreetmap.org/wiki/Stats). Regarding the coverage of the OpenStreetMap, it is well known that -- at least currently -- it is very uneven, and the level of detail varies significantly from location to location. This can, for example, be seen from the [interactive visualization](http://tyrasd.github.io/osm-node-density/#2/16.5/389.2) of node density by Martin Raifer, see also the [writeup](http://www.openstreetmap.org/user/tyr_asd/diary/22363). 

Instead of visualizing *all* elements on the latest version of the map, the purpose of `osm-timeslider` (this repo) is to give a way to visualize the *history* of the OSM; `osm-timeslider` makes it possible to selectively view elements that were last edited (or created) during a specific time period. The motivation for doing this is to give a way to better understand how the OpenStreetMap has evolved into its current state. However, to keep the scope of this work somehow under control, `osm-timeslider` will not consider all map elements. Rather, it will restrict to *amenities*, that is, map elements with an `amenity=..`-tag. These are one of the most frequently used tags on the OSM. Further, the visualizations are restricted to those amenities with c. 20k - 100k elements on the current map. General information about amenities and their use on the OpenStreetMap is collected on the [OSM wiki](http://wiki.openstreetmap.org/wiki/Key:amenity). Statistics about the most popular tags (including amenity tags) can be found on the [taginfo webpage](https://taginfo.openstreetmap.org/keys/amenity#values). 

`osm-timeslider` is browser-based and written using the [Leaflet library](http://leafletjs.com/). 

The below screenshots show examples of `osm-timeslider` in use. The first screenshot shows clinics in a region around Mali. Each clinic element (that is, each map element with an `amenity=clinic` tag) is shown as as a colored dot with the color indicating when the element was last edited (or created). For example, the teal colored dots represent map elements with a timestamp from 2013. Moreover, the slider on the bottom of the screen can be used to change the selected time period. In the clinic screenshot, the slider is set to display clinics from 2007 to the beginning of 2015. Clicking on a marker also displays further information about the map element.

The below list shows the amenities extracted by the `am-process-data.R` script found in the `./data` directory. The list shows those amenities with c. 20k - 100k elements in the current snapshot of the [OpenStreetMap](https://openstreetmap.org) (as of 10/2015). This list contains 27 amenities. 




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>amenity</th>
      <th>count</th>
      <th>taginfo link</th>
      <th>OSM wiki</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>drinking_water</td>
      <td>102003</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=drinking_water">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Ddrinking_water">link</a></td>
    </tr>
    <tr>
      <td>telephone</td>
      <td>92363</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=telephone">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dtelephone">link</a></td>
    </tr>
    <tr>
      <td>atm</td>
      <td>88541</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=atm">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Datm">link</a></td>
    </tr>
    <tr>
      <td>bar</td>
      <td>84452</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=bar">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dbar">link</a></td>
    </tr>
    <tr>
      <td>police</td>
      <td>78006</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=police">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dpolice">link</a></td>
    </tr>
    <tr>
      <td>fire_station</td>
      <td>77765</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=fire_station">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dfire_station">link</a></td>
    </tr>
    <tr>
      <td>townhall</td>
      <td>72106</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=townhall">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dtownhall">link</a></td>
    </tr>
    <tr>
      <td>parking_space</td>
      <td>70863</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=parking_space">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dparking_space">link</a></td>
    </tr>
    <tr>
      <td>hunting_stand</td>
      <td>69539</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=hunting_stand">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dhunting_stand">link</a></td>
    </tr>
    <tr>
      <td>vending_machine</td>
      <td>63925</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=vending_machine">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dvending_machine">link</a></td>
    </tr>
    <tr>
      <td>fountain</td>
      <td>57480</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=fountain">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dfountain">link</a></td>
    </tr>
    <tr>
      <td>library</td>
      <td>53209</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=library">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dlibrary">link</a></td>
    </tr>
    <tr>
      <td>doctors</td>
      <td>49252</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=doctors">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Ddoctors">link</a></td>
    </tr>
    <tr>
      <td>swimming_pool</td>
      <td>47310</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=swimming_pool">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dswimming_pool">link</a></td>
    </tr>
    <tr>
      <td>social_facility</td>
      <td>39005</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=social_facility">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dsocial_facility">link</a></td>
    </tr>
    <tr>
      <td>university</td>
      <td>37972</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=university">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Duniversity">link</a></td>
    </tr>
    <tr>
      <td>car_wash</td>
      <td>36432</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=car_wash">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcar_wash">link</a></td>
    </tr>
    <tr>
      <td>college</td>
      <td>31710</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=college">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcollege">link</a></td>
    </tr>
    <tr>
      <td>bus_station</td>
      <td>29907</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=bus_station">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dbus_station">link</a></td>
    </tr>
    <tr>
      <td>community_centre</td>
      <td>29471</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=community_centre">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dcommunity_centre">link</a></td>
    </tr>
    <tr>
      <td>marketplace</td>
      <td>29427</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=marketplace">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dmarketplace">link</a></td>
    </tr>
    <tr>
      <td>dentist</td>
      <td>29182</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=dentist">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Ddentist">link</a></td>
    </tr>
    <tr>
      <td>waste_disposal</td>
      <td>28252</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=waste_disposal">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dwaste_disposal">link</a></td>
    </tr>
    <tr>
      <td>theatre</td>
      <td>21498</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=theatre">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dtheatre">link</a></td>
    </tr>
    <tr>
      <td>taxi</td>
      <td>21489</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=taxi">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dtaxi">link</a></td>
    </tr>
    <tr>
      <td>clinic</td>
      <td>19927</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=clinic">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dclinic">link</a></td>
    </tr>
    <tr>
      <td>parking_entrance</td>
      <td>19479</td>
      <td><a href="https://taginfo.openstreetmap.org/tags/amenity=parking_entrance">link</a></td>
      <td><a href="https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dparking_entrance">link</a></td>
    </tr>
  </tbody>
</table>



A more detailed description of how the amenity map elements were extracted is given in the [README](./data/README.md) file in the `data` directory.

## Screenshots

### Clinics in Mali

![](./images/clinic.png)

### Townhalls in the USA

![](./images/townhall.png)

The Geographic Names Information System (GNIS) is a database of millions of geographic features in the USA. This was imported into the OSM in 2009, see the [OSM wiki](http://wiki.openstreetmap.org/wiki/USGS_GNIS). In the United States, these database imports can be seen for many of the amenities listed above. These kinds of large database imports can be seen as large point clouds suddenly appearing (or disappearing) when moving the slider. The orange dots in the above screenshot show townhall amenities with a timestamp from 2009. The red dots are townhalls in Boston with a timestamp from 2008, see changeset [143731](http://www.openstreetmap.org/changeset/143731).

### Police stations in Japan/South Korea

![](./images/police.png)

South Korea divides into two regions. The orange dots (in the south) represent police stations with a timestamp from 2009. The teal dots (in the north) represent police stations with a timestamp from 2012. Similarly, the green dots (in the south of Japan) represent police stations with a timestamp from 2011. 

### License 

The above table and images are generated using data from the [OpenStreetMap](https:/openstreetmap.org) project. The OSM data is © OpenStreetMap contributors, and it is available under the terms of the [ODbL](https://www.openstreetmap.org/copyright). Maps are drawn using the [Leaflet library](http://leafletjs.com/) using the [Positron tiles](https://cartodb.com/basemaps), tiles © CartoDB, CC BY 3.0. 

For further license information, see the [LICENSE.md](LICENSE.md) file.
