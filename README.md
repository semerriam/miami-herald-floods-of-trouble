# miami-herald-floods-of-trouble

South Florida's flooding crisis has intensified in recent years, driven by a combination of sea level rise, aging stormwater infrastructure, and increasingly severe rain events. This repository contains the datasets behind the Miami Herald's *Floods of Trouble* series, which documented how residents across Miami-Dade and Broward counties experienced flooding in their neighborhoods. The series was reported by [Alex Harris](https://www.miamiherald.com/profile/218643730/) and [Susan Merriam](https://www.miamiherald.com/profile/291545305/). 

The series was part of the [Pulitzer Center's Connected Coastlines](http://pulitzercenter.org/connected-coastlines/) nationwide reporting initiative.

## Read the series

- ['Street is lake, urgent!' Herald mapping reveals flooding blind spots](https://www.miamiherald.com/news/local/environment/climate-change/article311515845.html) — November 12, 2025
- [The unseen flooding risk in South Florida: Rising water beneath our feet](https://www.miamiherald.com/news/local/environment/climate-change/article307805065.html) — June 10, 2025
- [How secret flood histories cost Florida home buyers and mask state's risk](https://www.miamiherald.com/news/local/environment/climate-change/article288475951.html) — April 24, 2025
- [Climate change is coming for Florida's real estate. Why don't prices reflect it?](https://www.miamiherald.com/news/local/environment/climate-change/article303949086.html) — May 6, 2025
- [Thousands of Florida homes have flooded before. Tips to avoid buying one](https://www.miamiherald.com/news/local/environment/climate-change/article304382966.html) — April 24, 2025
- [From the sky, the ground, the sea. The three ways South Florida gets flooded](https://www.miamiherald.com/news/local/environment/climate-change/article307805040.html) — June 10, 2025
- [See what flooding does to South Florida: 100 places, 100 photos](https://www.miamiherald.com/news/local/environment/climate-change/article312642545.html) — November 12, 2025
- [Is your South Florida street flooded? How to let the right people know](https://www.miamiherald.com/news/local/environment/climate-change/article312856124.html) — November 12, 2025
- [How we reported and mapped South Florida's (many) flood complaints](https://www.miamiherald.com/news/local/environment/climate-change/article312614074.html) — November 12, 2025

## How we got this data

Flooding doesn't stop at city limits. The data meant to track it often does. That simple mismatch — between where water goes and how governments measure it — has long left South Florida with an incomplete picture.

To document it, the Herald sought flood complaints and service requests from multiple municipalities in Miami-Dade and Broward counties. The responses were just as varied as the governments and communities they serve. Some small municipalities, like El Portal and Miami Shores, don't even track flood-related complaints or service requests. Monroe County, one of the most flood-prone spots in the nation, does not explicitly track flood complaints. The five datasets below reflect the records we were able to obtain.

Our analysis is somewhat piecemeal, constrained by data divided along municipal boundaries and shaped by differing collection methods. It almost certainly reflects an underestimate of flooding across the region, perhaps a dramatic one.

Full details on our reporting and data methodology are in [How we reported and mapped South Florida's (many) flood complaints](https://www.miamiherald.com/news/local/environment/climate-change/article312614074.html).

## A note on anonymization

The datasets in this repository have been reviewed and stripped of personally identifiable information before publication. This includes submitter names, comments, email addresses, and phone numbers that appeared in the original records provided by government agencies.

One dataset — City of Hollywood flooding service requests — originally contained records submitted with first and last names and phone numbers attached. Those fields have been removed entirely. The City of Coral Gables records originally included customer email addresses, which have also been removed. All other identifying fields that appeared in the raw data but are not present here were excluded for the same reason.

## Get the data

Files are available in both GeoJSON and CSV formats in this repository.

To download:
- Clone this repository
- Download the entire directory as a zip file
- Download individual files by clicking the file, then clicking the **Download raw file** button

All five datasets contain point geometries (latitude/longitude) representing the location of the reported flooding incident or service request.

Have questions or spot an error? Researchers seeking access to the unredacted source data may contact Susan Merriam at [susan.e.merriam@gmail.com](mailto:susan.e.merriam@gmail.com) with a brief description of their project and intended use.

Use of this data is granted to researchers, journalists, and the public under an [MIT License](LICENSE).

Please credit all uses to: *the Miami Herald* or *an analysis by the Miami Herald* with a link back to our reporting.

---

## Data dictionary

### `miami_dade_data` — Miami-Dade County / City of Miami 311 flood complaints
13,296 records | January 2016 – February 2024

Miami-Dade County provided the Herald with a dataset of 13,296 service requests. 10,271 service requests were labeled as “Storm Flood/Drainage” within the City of Miami and 3,025 service requests were labeled as “Flooding/Standing Water - Localized” from the entirety of Miami-Dade county. The data provided was from January 2016 to February 2024. While a vast majority of the requests included GPS coordinates, 27 records were manually geocoded using Google Maps based on the addresses provided in the data. Some of the county-wide data is available to the public on the [Miami-Dade County’s Open Data Hub](https://gis-mdc.opendata.arcgis.com/search?q=311+Service+Requests+-+Miami-Dade+County). The City of Miami communicated to the Herald that the flood-related service requests were submitted through various methods. Residents submitted requests to the 311 Call Center, [Miami.gov](https://www.miami.gov/My-Home-Neighborhood/Solve-a-Problem/Report-Flooding) and [Miami-Dade County web pages](https://www.miamidade.gov/environment/flood-complaints.asp), [ISeeChange](https://tracker.iseechange.com/miami/welcome), made phone calls to City Department staff, Commissioner Offices staff, and Mayor Office staff.

| field | description |
| --- | --- |
| type_description | complaint type (`FLOODING / STANDING WATER - LOCALIZED` or `STORM FLOOD/ DRAINAGE`) |
| created_date | date the 311 complaint was submitted |
| full_address | street address associated with the complaint |
| unit | unit number, if applicable |
| city | city within Miami-Dade County (often null; `full_address` is more complete) |
| zip_code | ZIP code of the complaint location |
| latitude | latitude of the complaint location |
| longitude | longitude of the complaint location |
| date | date of the complaint, normalized to ISO 8601 format |

---

### `coral_gables_data` — City of Coral Gables drainage service requests
869 records | February 2015 – December 2023

In response to the Herald’s public records request, the City of Coral Gables provided 877 reports related to flooding and drainage issues filed between February 2015 and December 2023. Residents [submitted these reports](https://www.coralgables.com/flood-protection-and-insurance) through the city’s online portal or by phone, and the city shared the resulting records in multiple PDF files. Those files were processed using optical character recognition (OCR) in Adobe Acrobat, converted into Excel spreadsheets, geocoded with [Geoapify](https://www.geoapify.com/tools/geocoding-online/) and analyzed in a Python notebook. Some reports were removed from the dataset because their GPS locations fell outside the city boundaries or their assigned departments appeared unrelated to flooding—covering issues such as internal permits, right-of-way work, and solid waste.

| field | description |
| --- | --- |
| original_reference_no | unique reference number assigned by the city's work-order system |
| original_request_type | category of the service request (e.g., `Storm Drain/ Catch Basin`, `Drainage Assessments/Improvements`) |
| original_status | status of the request at time of data export (`Completed`, `Assigned`, etc.) |
| original_priority | priority level assigned to the request |
| original_assigned_dept | city department assigned to handle the request |
| original_date | date and time the request was submitted |
| formatted | geocoded full address string |
| lat | latitude of the service request location |
| lon | longitude of the service request location |

---

### `broward_data` — Broward County crowd-sourced flood reports
923 records | October 2016 – November 2023

Broward County provided the Herald a geopackage file of the county’s [Document the Floods dashboard](https://document-the-floods-bcgis.hub.arcgis.com/); the dataset included 923 reports of flooding at 827 unique locations indicating that there were multiple reports submitted from the same locations. The data covers from October 2016 to November 2023.

| field | description |
| --- | --- |
| address | street address or location description of the reported flood |
| commission_district | Broward County commission district number |
| date_and_time | date and time of the flood report submission |
| flood_depth_measured_here | type of location where flood depth was observed (e.g., `parking_lot`, `storm_drain`, `road`) |
| flood_depth_measured_here_other | free-text description when `other` is selected above |
| flood_type | cause of flooding (e.g., `high_tide_tidal_flooding`, `rainfall_storm_hurricane`) |
| has_this_location_flooded | reporter's characterization of flood frequency (`often`, `sometimes`, `once_or_twice`) |
| municipality | municipality within Broward County where the event occurred |
| what_properties_are_flooded | type of properties affected (`Private`, `Commercial`, `Public`) |
| what_properties_are_flooded_oth | free-text description when `other` property type is selected |
| water_depth_in_inches | reported flood water depth in inches |
| zip_code | ZIP code of the reported location |
| temperature | ambient temperature at time of report (often null) |
| atmospheric_pressure | atmospheric pressure at time of report (often null) |
| air_humidity | relative humidity at time of report (often null) |
| wind_speed | wind speed at time of report (often null) |
| wind_gust | wind gust speed at time of report (often null) |
| wind_direction | wind direction at time of report (often null) |
| longitude | longitude of the reported location |
| latitude | latitude of the reported location |
| horizontal_accuracy | GPS horizontal accuracy in meters (often null) |
| date | date of the report, normalized to ISO 8601 format |

---

### `hollywood_data` — City of Hollywood flooding service requests
317 records | July 2021 – May 2024

Through a public records request, the Herald was provided a dataset of over 3,000 service requests for the City of Hollywood. When filtered to requests relating to flooding and flooding-related issues, the Herald found 317 relevant requests covering a timeframe from July 2021 to May 2024. According to the City Clerk's office, requests were reported through [Hollywood Connect](https://www.hollywoodfl.org/744/Hollywood-Connect), the city's portal for reporting non-emergency concerns.

| field | description |
| --- | --- |
| request_type | type of service request (all records: `Flooding Issues`) |
| Address | street address of the reported flooding |
| AdditionalData | system-generated field confirming request type selection |
| StatusType | current status of the request (`Completed`, `Received`, `Duplicate`, etc.) |
| InitialBoundaryName | geographic and administrative boundaries associated with the location, including city limits, commission district, and code enforcement zone |
| date | date and time the request was submitted |
| Latitude | latitude of the reported location |
| Longitude | longitude of the reported location |

---

### `ft_lauderdale_data` — City of Fort Lauderdale stormwater inspection work orders
1,174 records | April – May 2023

Through a public records request, the Herald was provided a dataset of 1,174 [hazard report requests](https://gis.fortlauderdale.gov/hazardreports/) from April to May of 2023, when the “1,000-year flood” occurred, placing much of Fort Lauderdale underwater for days. The requests were submitted through the city’s [Lauderserv](https://gis.fortlauderdale.gov/lauderservgis/) system. The Herald geocoded the records provided using the Google Maps Geocoding API.

| field | description |
| --- | --- |
| request_id | unique identifier for the work order |
| request_type | type of inspection or service request (all records: `Stormwater Inspection`) |
| create_date | date and time the work order was created |
| close_date | date and time the work order was closed or resolved |
| address | street address of the inspection location |
| name | full address string including city and state |
| latitude | latitude of the inspection location |
| longitude | longitude of the inspection location |
