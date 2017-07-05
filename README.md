####Arma 3: Exile Mod: Vehicle Protection System by ynpmoose of ZeroSurvival.com

Updated for Exile 1.0.3 "Lemon" - 05Jul2017

Updated for Exile 1.0.1 "Sweet Potato" - 31Aug2016

Updated for Exile 0.9.8 "Kiwi" - 29Jun2016 (ExileServer_object_vehicle_network_unlockVehicleRequest.sqf also removed because it never actually did anything.)

Updated for Exile 0.9.6 "Pomelo" - 07Mar2016

This is a collection of scripts changes for the Exile Mod for Arma 3.This was built off of a basic protection system created by NoKturnal Gaming Community *NGC* that was posted to the ExileMod.com forums by gmctyphoon92. Their base scripts made vehicles invincible on restart until unlocked by a player with the code.
http://www.exilemod.com/topic/8873-disappearing-vehicles-on-restarts/?do=findComment&comment=58814


**Vehicle Protection System Features:**
- All persistent vehicles are invincible on server restart, but only if they are locked in a territory where the owner has build permissions.
- Unlocked vehicles, or vehicles left in the wild can be destroyed.
- If the vehicle owners logs in, all owned vehicles are vulnerable until restart.
- If a friend with the code uses one of your vehicles, that specific vehicle is vulnerable until restart.
- Vehicles in Trader Zones are unlocked on restart per Exile default.


**Installation intructions:**
These instructions assume that there are no other no other scripts modified in your base Exile installation. If there are other changes that touch the same .SQF files, you will need to manually merge the changes. All the code for the Vehicle Protection System is clearly wrapped in comments to make it easy to find.

- Download the files from http://github.com/ynpmoose/A3ExileVPS

- Shutdown the A3Exile Server Down and locate you Mission PBO (Example: \Exile Server\@ExileServer-0.9.41\Arma 3 Server\mpmissions\Exile.Altis.pbo)

- Extract PBO files using PBO Manager

- Edit config.cpp using something like Notepad++

- Locate the class CfgExileCustomCode and add your overrides, something like this:

```
	class CfgExileCustomCode
		{
		/*
			You can overwrite every single file of our code without touching it.
			To do that, add the function name you want to overwrite plus the 
			path to your custom file here. If you wonder how this works, have a
			look at our bootstrap/fn_preInit.sqf function.
	
			Simply add the following scheme here:
	
			<Function Name of Exile> = "<New File Name>";
	
			Example:
	
			ExileClient_util_fusRoDah = "myaddon\myfunction.sqf";
		*/
		//Vehicle Protection System
		ExileServer_object_player_database_load = "overrides\ExileServer_object_player_database_load.sqf";
		ExileServer_object_vehicle_database_load = "overrides\ExileServer_object_vehicle_database_load.sqf";
		ExileServer_object_vehicle_database_update = "overrides\ExileServer_object_vehicle_database_update.sqf";
		};
```

- Create a folder in your mission called 'overrides'

- Copy the .SQF files from the downloaded zip in this overrides folder

- Use PBO Manager to repack your PBO

- Restart the Exile Server
