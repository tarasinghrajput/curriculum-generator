# Curriculum Generator

metadata:
  openclaw:
    emoji: 📚
    type: multi_agent
    capabilities:
      - curriculum_design
      - resource_research
      - sheet_creation
    agents_used:
      - researcher
      - comms
    tools:
      - web_search
      - gog
      - message
    timeout: 1800

## Purpose
Generate structured curricula following the SOP pattern, creating Google Sheets with resources organized by clusters.

## Trigger Keywords
- "curriculum"
- "curriculum for"
- "generate curriculum"
- "create curriculum"
- "build curriculum"

## Workflow

### Phase 1: Collect Requirements (Anukar Core)

Ask the user these questions:

1. **Target POD Type**
   ```
   Which POD type is this curriculum for?
   - P0 (Beginner, 6-12 months)
   - P1 (Intermediate, 3-6 months)
   - P2 (Advanced, 1-3 months)
   - P3 (Expert, < 1 month)
   ```

2. **Content Focus**
   ```
   What is the main focus area?
   - Coding fundamentals
   - Web development
   - Data science
   - Mobile development
   - Other (please specify)
   ```

3. **Content Type Preference**
   ```
   What content types to include?
   - Video tutorials
   - Reading materials
   - Hands-on exercises
   - Projects
   - All of the above
   ```

4. **Duration** (Optional)
   ```
   Expected duration? (1 week, 2 weeks, 1 month, 3 months)
   ```

5. **Specific Topics** (Optional)
   ```
   Any specific topics to include?
   ```

### Phase 2: Research Resources (Researcher Agent)

After collecting answers, spawn researcher with collected requirements.

See: prompts/researcher-task.md

### Phase 3: Create Sheet (Comms Agent)

After researcher completes, spawn comms with research data.

See: prompts/comms-task.md

### Phase 4: Deliver (Anukar Core)

1. Receive sheet URL from comms
2. Send to user on Telegram:
   ```
   📚 Curriculum Generated!

   📋 Name: [Curriculum Name]
   🎯 Target: [POD Type]
   📦 Clusters: [X]
   🔗 Resources: [Y]

   📊 Sheet: [URL]
   ```
3. Log completion to dashboard

## Sheet Storage

- **Folder ID:** 1upJQu-IVmZRJQsNGmJNRzq9IwL67MVL9
- **Folder URL:** https://drive.google.com/drive/folders/1upJQu-IVmZRJQsNGmJNRzq9IwL67MVL9

## Sheet Naming Convention

Format: `Curriculum_[POD]_[Topic]_[YYYY-MM-DD]`

Examples:
- Curriculum_P0_WebDevelopment_2026-02-22
- Curriculum_P1_PythonBasics_2026-02-22
- Curriculum_P2_DataScience_2026-02-22

## Sheet Columns

| Column | Header | Example |
|--------|--------|---------|
| A | Curriculum ID | CUR-2026-02-22-001 |
| B | File Name | Curriculum_P0_WebDev_2026-02-22 |
| C | Target POD Type | P0 |
| D | Clusters | HTML Basics, CSS Fundamentals |
| E | Content Type | Video |
| F | Covered Topics | HTML tags, elements |
| G | Owner | Anukar |
| H | Resource Link | https://youtube.com/... |
| I | Document Created | 2026-02-22 |
| J | Last Updated On | 2026-02-22 |

## Example Usage

User: "Generate curriculum for P0 PODs on web development"

Anukar:
1. Asks clarifying questions
2. Spawns researcher to find resources
3. Spawns comms to create sheet
4. Sends sheet link to user

## Notes

- Always use the designated folder for sheet storage
- Follow naming convention strictly
- Log all agent tasks to dashboard
- Validate resources before including
- Default to free resources unless specified
