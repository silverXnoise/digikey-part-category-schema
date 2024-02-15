# DigiKey Part Category Schema

An effectively 1:1 representation of DigiKey part categories for use in InvenTree.

## Instructions for importing

**NOTE**: This is intended to be integrated into a new instance with a blank database. Merging with existing data has _not_ been tested, do so at your own risk!

InvenTree documentation for importing data can be found at [https://docs.inventree.org/en/0.13.5/settings/import/](https://docs.inventree.org/en/0.13.5/settings/import/).

In order to import the entire schema, the import limits in `/home/inventree/InvenTree/InvenTree/admin.py` need to be raised. They are set to 1000 rows and 100 columns by default, you should only need to raise the row limit from 1000 to 1500.

Use whichever file format suits your needs/comfort level. Category imports are completed using the InvenTree API, which supports all of the formats found in this repo, regardless of your particular database flavor. All datasets were originally developed and tested using InvenTree v0.13.5. 

**Important**: Be sure to change/remove the Default Location IDs for each category array (use basic find/replace).

## Idle curiosity

To make these schema files, I used the DigiKey API to pull its categories and dump them into a `json` document. The InvenTree part category schema is not too dissimilar to DigiKey's, however DigiKey uses nested `json` where InvenTree's was flat, so the most finicky task involved using a lot of `json` filtering, `regex`, and find/replace to get everything flattened out. The only keys from the DigiKey dataset that could be included were the category ID, category name, and parent ID. To ensure a successful import, the remaining data was added with blank or generic values. InvenTree then helpfully used the relationship with the parent IDs, and filled in some of the missing pieces, such as parent name and category path.

## Credits

All credit and gratitude goes to the [devs](https://github.com/inventree/InvenTree/graphs/contributors) at InvenTree for their hard work and dedication to this incredibly useful and generously spec'd platform! Please help [support](https://github.com/InvenTree/InvenTree/#heart-support) them in any way you can by visiting their [website](https://inventree.org/) and [getting involved](https://github.com/InvenTree/InvenTree/#wave-contributing)!

## Contributing

If anyone knows how to flesh things out to an even greater extent, please open a PR with your results!

## Disclaimer

This dataset was created by a very tired and marginally skilled individual who's hoping it will be helpful to other epic nerds such as himself. It does not include any warranty, implied or not, and if used improperly it may damage your system, any data contained therein, and/or your fragile self-esteem. Please use care when importing data--always make a backup--and consider employing someone else to blame in the unlikely event of catastrophic error(s).
