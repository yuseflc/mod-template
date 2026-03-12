<div align="center">

# Minecraft Forge Mod Template

[![Java Version](https://img.shields.io/badge/Java-17-orange.svg?style=flat-square&logo=java)](https://adoptium.net/temurin/releases/?version=17)
[![Minecraft](https://img.shields.io/badge/Minecraft-1.20.x-588265.svg?style=flat-square&logo=minecraft)](https://minecraft.net/)
[![Forge](https://img.shields.io/badge/Forge-47.4.16-dfa338.svg?style=flat-square)](https://files.minecraftforge.net/)
[![Gradle](https://img.shields.io/badge/Gradle-8.x-02303A.svg?style=flat-square&logo=gradle)](https://gradle.org/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](#license)

*A clean, modern, and ready-to-use template for Minecraft Forge mod development using Parchment mappings.*

</div>

---

## Table of Contents
- [Requirements](#requirements)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [.gitignore Configuration](#gitignore-configuration)
- [Configuration](#configuration)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)

---

## Requirements

Before you begin, ensure you have met the following requirements:
*   **[Java Development Kit (JDK) 17](https://adoptium.net/temurin/releases/?version=17)** or higher (Eclipse Temurin is recommended)
*   **[Git](https://git-scm.com/downloads)** (for version control)
*   An IDE of your choice (**[IntelliJ IDEA Community](https://www.jetbrains.com/idea/download/)** is highly recommended)

---

## Quick Start

Get your development environment running in just a few minutes:

### 1. Clone the repository
```bash
git clone <your-repository-url>
cd mod-template
```

### 2. Build the project
```bash
# On Windows
gradlew build

# On Linux/Mac
./gradlew build
```

### 3. Launch the game
```bash
# Launch Minecraft Client
./gradlew runClient

# Launch Minecraft Server
./gradlew runServer
```

---

## Project Structure

Here is a quick overview of the essential files and folders in this template:

```text
mod-template/
 ├── src/
 │    ├── main/
 │    │    ├── java/        # Your mod's source code goes here
 │    │    └── resources/   # Textures, models, sounds, and recipes
 │    ├── test/             # Unit testing
 │    └── generated/        # Auto-generated resources (from runData)
 ├── gradle/                # Gradle wrapper files
 ├── run/                   # Client execution directory (sandbox)
 ├── run-data/              # Data generation sandbox
 ├── build.gradle           # Main build script and dependencies
 ├── gradle.properties      # Project variables (Minecraft version, Mod ID, etc.)
 └── settings.gradle        # Gradle project settings
```

---
## .gitignore Configuration

This template includes a carefully configured `.gitignore` that filters out files unnecessary for development while preserving template essentials:

### Excluded from Git
- **`build/`** - Compiled classes and artifacts (regenerated on build)
- **`run/logs/`** - Client/Server logs
- **`run/saves/`** - Minecraft world saves
- **`run/mods/`** - Downloaded mods
- **IDE files** - `.idea/`, `*.iml`, etc. (IntelliJ)
- **OS files** - `.DS_Store`, `Thumbs.db`, etc.

### Included in Git (Important for Template)
- **`run/config/`** - Mod configuration files
- **`run/defaultconfigs/`** - Default configuration templates
- **`src/`** - All source code and resources
- **Gradle files** - `gradle/`, `build.gradle`, `gradle.properties`

**Note:** The `build/` directory is safe to exclude because it regenerates automatically when you run `./gradlew clean build` or any gradle task.

---
## Configuration

All the main configuration happens inside the `gradle.properties` file. It's the central hub for your mod's identity.

### Mod Metadata
Change these values to match your mod:
```properties
mod_id=examplemod
mod_name=Example Mod
mod_version=0.0.1
mod_authors=yourname
mod_group_id=com.yourname.examplemod
mod_description=Example Mod by yourname

```

### Minecraft & Forge Versions
```properties
minecraft_version=1.20.1
forge_version=47.4.16
mapping_channel=parchment
mapping_version=2024.02.18-1.20.1
```
> **Note:** This template uses **[Parchment](https://parchmentmc.org/)** mappings by default for highly readable parameter names and Javadocs. Check their **[documentation](https://parchmentmc.org/)** for version changes.

---

## Development

### Adding Dependencies (like JEI)
Open `build.gradle` and locate the `dependencies {}` block. You can easily add external mods:

```groovy
dependencies {
    minecraft "net.minecraftforge:forge:${minecraft_version}-${forge_version}"
    
    // Example: Adding Just Enough Items (JEI)
    // compileOnly fg.deobf("mezz.jei:jei-${minecraft_version}-common-api:${jei_version}")
    // runtimeOnly fg.deobf("mezz.jei:jei-${minecraft_version}-forge:${jei_version}")
}
```

### Essential Gradle Commands

| Task | Command | Description |
| :--- | :--- | :--- |
| **Clean** | `./gradlew clean` | Deletes the `build/` directory |
| **Build** | `./gradlew build` | Compiles code and packages the mod `.jar` |
| **DataGen** | `./gradlew runData` | Runs data generators (recipes, loot tables) |
| **IDE Setup**| `./gradlew genIntellijRuns`| Re-generates IntelliJ run configurations |

### Known Build Warnings

When syncing or building the project, you might see the following warnings in your console. **Both are completely harmless and can be safely ignored:**

1. **`Deprecated Gradle features were used in this build...`**
   This is caused by internal Forge plugins (like ForgeGradle) using older Gradle APIs. It does not affect your mod. This template hides these warnings by default using `org.gradle.warning.mode=none` in `gradle.properties`.
2. **`Cannot resolve resource filtering of MatchingCopyAction...`**
   This is a known visual bug in IntelliJ IDEA when it encounters the `expand` logic in `build.gradle` (used to replace properties in `mods.toml`). Since IntelliJ delegates the actual build process to Gradle by default, this warning will not cause any issues or failed builds.

---

## Contributing

Contributions, issues, and feature requests are welcome!
Feel free to check the **[issues page](https://github.com/yuseflc/mod-template/issues)** if you want to report a bug, request a new feature, or let me know about outdated dependencies.

---

## License

This project is licensed under the **MIT License** - see the [LICENSE.md](LICENSE.md) file for details.

---

<div align="center">
  <b>Created by <a href="https://github.com/yuseflc">yuseflc</a></b>
</div>