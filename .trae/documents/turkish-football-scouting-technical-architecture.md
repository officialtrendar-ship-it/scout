# Turkish Football Scouting Web Application - Technical Architecture Document

## 1. Architecture Design

```mermaid
graph TD
  A[User Browser] --> B[Single HTML File Application]
  B --> C[Inline CSS Styles]
  B --> D[Inline JavaScript]
  B --> E[Form Elements & DOM]

  subgraph "Client-Side Application"
    B
    C
    D
    E
  end

  subgraph "Browser APIs"
    F[DOM API]
    G[CSS Media Queries]
    H[Print API]
  end

  B --> F
  C --> G
  B --> H
```

## 2. Technology Description

- Frontend: Vanilla HTML5 + CSS3 + JavaScript (ES6+)
- Backend: None (client-side only application)
- External Dependencies: None (no libraries or frameworks)

## 3. Route Definitions

| Route | Purpose |
|-------|---------|
| / (index.html) | Single-page application containing all scouting functionality |

Note: This is a single-page application without routing. All functionality is contained within one HTML file with different sections managed through DOM manipulation and CSS styling.

## 4. API Definitions

This application does not include backend services or external APIs. All functionality is handled client-side through JavaScript DOM manipulation and form interactions.

## 5. Data Model

### 5.1 Data Model Definition

The application uses client-side JavaScript objects to manage form data temporarily during user interaction. No persistent storage is implemented in Phase 1.

```mermaid
erDiagram
  PLAYER_REVIEW {
    string general_overview
    string technical_tactical_strengths
    string development_areas
    string physical_mental_characteristics
  }
  
  MATCH_REPORT {
    string left_team_name
    number left_team_score
    string right_team_name
    number right_team_score
    string scout_name
    string tournament_name
    string weather_conditions
    string stadium
    string pitch_conditions
    date match_date
  }
  
  TEAM_SHEET {
    string left_technical_director
    string right_technical_director
    array left_team_players
    array right_team_players
  }
  
  PLAYER_ENTRY {
    string player_number
    string player_name
    string substitution
    string goals
    string rating
  }
```

### 5.2 Data Structure Implementation

The application uses JavaScript objects to temporarily store form data:

```javascript
// Player Review Data Structure
const playerReview = {
  generalOverview: '',
  technicalTacticalStrengths: '',
  developmentAreas: '',
  physicalMentalCharacteristics: ''
};

// Match Report Data Structure
const matchReport = {
  leftTeamName: '',
  leftTeamScore: 0,
  rightTeamName: '',
  rightTeamScore: 0,
  scoutName: '',
  tournamentName: '',
  weatherConditions: '',
  stadium: '',
  pitchConditions: '',
  matchDate: ''
};

// Team Sheet Data Structure
const teamSheet = {
  leftTechnicalDirector: '',
  rightTechnicalDirector: '',
  leftTeamPlayers: Array(16).fill({
    number: '',
    name: '',
    substitution: '',
    goals: '',
    rating: ''
  }),
  rightTeamPlayers: Array(16).fill({
    number: '',
    name: '',
    substitution: '',
    goals: '',
    rating: ''
  })
};
```

Note: Phase 2 will implement localStorage for data persistence and export functionality.